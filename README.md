<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
<body>
    <h1>🏥 Hospital System Simulation Model</h1>
    
    <h2>1. Brief Overview</h2>
    <p>A comprehensive hospital system model with 7 interconnected departments handling two patient categories:</p>
    <ul>
        <li>⚕️ <strong>Elective Patients</strong> (75%): Scheduled care pathway</li>
        <li>🚨 <strong>Urgent Patients</strong> (25%): Emergency care pathway</li>
    </ul>

    <h2>2. Hospital Departments & Bed Capacity</h2>
    <table>
        <tr><th>Department</th><th>Beds</th></tr>
        <tr><td>Pre-Operative Unit</td><td>25</td></tr>
        <tr><td>Emergency Room (ER)</td><td>10</td></tr>
        <tr><td>Laboratory</td><td>3 stations</td></tr>
        <tr><td>Operating Rooms (ORs)</td><td>50</td></tr>
        <tr><td>General Ward</td><td>40</td></tr>
        <tr><td>ICU</td><td>10</td></tr>
        <tr><td>CCU</td><td>5</td></tr>
    </table>

    <h2>3. Patient Flow Dynamics</h2>
    <h3>3.1 Arrival Patterns</h3>
    <pre>
- Elective: λ = 1/hr (Poisson)
- Urgent:  λ = 4/hr (Poisson)
- Group arrivals: 0.5% urgent (2-5 patients)
- ER Queue Limit: 10 patients</pre>

    <h3>3.2 Testing Process</h3>
    <ul>
        <li>🕒 Administrative Wait:
            <ul>
                <li>Elective: 60min</li>
                <li>Urgent: 10min</li>
            </ul>
        </li>
        <li>🧪 Lab Testing:
            <ul>
                <li>Time: U(28,32) min</li>
                <li>Priority: Urgent > Elective</li>
            </ul>
        </li>
    </ul>

    <h2>4. Surgical Operations</h2>
    <pre>
⚕️ OR Setup: 10min between surgeries
🔀 Surgery Distribution:
    - Simple:     50% (Appendectomy etc.)
    - Moderate:   45% (Cholecystectomy etc.)
    - Complex:     5% (Open-heart surgery)</pre>

    <h2>5. Post-Operative Routing</h2>
    <table>
        <tr><th>Surgery Type</th><th>Destination</th></tr>
        <tr><td>Simple</td><td>General Ward (100%)</td></tr>
        <tr><td>Moderate</td><td>GW (70%) | ICU (10%) | CCU (20%)</td></tr>
        <tr><td>Complex</td><td>ICU (75%) | CCU (25%)</td></tr>
    </table>

    <h2>6. Critical Care Parameters</h2>
    <ul>
        <li>⏳ Stay Duration:
            <ul>
                <li>General Ward: Exp(μ=50h)</li>
                <li>ICU/CCU: Exp(μ=25h)</li>
            </ul>
        </li>
        <li>⚠️ Complications:
            <ul>
                <li>1% ICU/CCU deterioration</li>
                <li>10% surgical mortality</li>
            </ul>
        </li>
    </ul>

    <h2>7. Emergency Scenarios</h2>
    <pre>
⚡ Power Outages:
    - Monthly random occurrence
    - Generators support:
        • 100% OR capacity
        • 80% ICU/CCU capacity</pre>

    <h2>8. System Workflow</h2>
    <blockquote>
    <strong>Elective Pathway:</strong><br>
    Pre-Op → Lab → Pre-Op (48h) → OR → Post-Op → Discharge<br><br>
    <strong>Urgent Pathway:</strong><br>
    ER → Lab → ER (Tri(5,75,100) min) → OR → ICU/CCU/GW → Discharge
    </blockquote>

    <hr>
    <p><em>Note: Model parameters can be calibrated using historical hospital data for specific implementations.</em></p>
</body>
</html>
