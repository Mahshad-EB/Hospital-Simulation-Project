<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hospital System Problem Formulation</title>
</head>
<body>
    <h1>Hospital System Problem Formulation</h1>
    <p><em>(Collaboratively developed with a classmate)</em></p>

    <h2>1. Brief Overview</h2>
    <p>This document outlines a detailed hospital system model comprising seven interconnected departments. The system manages two patient categories (elective and urgent) with distinct arrival patterns, prioritization rules, and treatment pathways. Key challenges include resource allocation, patient routing under uncertainty, and handling critical scenarios like power outages.</p>

    <h2>2. Hospital Departments & Bed Capacity</h2>
    <table>
        <tr>
            <th>Department</th>
            <th>Number of Beds</th>
        </tr>
        <tr><td>1. Pre-Operative Unit</td><td>25</td></tr>
        <tr><td>2. Emergency Room (ER)</td><td>10</td></tr>
        <tr><td>3. Laboratory</td><td>3</td></tr>
        <tr><td>4. Operating Rooms (ORs)</td><td>50</td></tr>
        <tr><td>5. General Ward</td><td>40</td></tr>
        <tr><td>6. Intensive Care Unit (ICU)</td><td>10</td></tr>
        <tr><td>7. Cardiac Care Unit (CCU)</td><td>5</td></tr>
    </table>

    <h2>3. Patient Classification & Arrival Process</h2>
    <h3>3.1 Patient Types</h3>
    <ul>
        <li><strong>Elective Patients (75%):</strong> Scheduled in advance, admitted to the Pre-Operative Unit 2 days before surgery.</li>
        <li><strong>Urgent Patients (25%):</strong> Require immediate care, prioritized for surgery. Admitted via the ER.</li>
    </ul>

    <h3>3.2 Arrival Rates</h3>
    <ul>
        <li><strong>Elective Patients:</strong> Poisson arrival rate of 1 patient/hour</li>
        <li><strong>Urgent Patients:</strong> Poisson arrival rate of 4 patients/hour
            <ul>
                <li><strong>Group Arrivals:</strong> 0.5% arrive in groups of 2–5 (uniform distribution) if ER capacity allows</li>
                <li><strong>ER Queue Limit:</strong> Maximum 10 patients in ambulances</li>
            </ul>
        </li>
    </ul>

    <h2>4. Testing Process</h2>
    <h3>Administrative Wait Time</h3>
    <ul>
        <li>Elective (Pre-Operative): 60 minutes</li>
        <li>Urgent (ER): 10 minutes</li>
    </ul>

    <h3>Laboratory Testing</h3>
    <ul>
        <li>Testing time: Uniform distribution (28–32 minutes)</li>
        <li>Priority: Urgent > Elective</li>
    </ul>

    <h3>Post-Testing Routing</h3>
    <ul>
        <li>Elective: Return to Pre-Operative Unit (2 days) → OR</li>
        <li>Urgent: ER (Triangular wait: min=5, mode=75, max=100 mins) → OR</li>
    </ul>

    <h2>5. Surgery Process</h2>
    <h3>5.1 OR Setup</h3>
    <ul>
        <li>Setup Time: 10 minutes between surgeries</li>
        <li>Prioritization: Urgent > Elective</li>
    </ul>

    <h3>5.2 Surgery Types & Distribution</h3>
    <table>
        <tr><th>Surgery Type</th><th>Probability</th></tr>
        <tr><td>Simple (e.g., appendectomy)</td><td>50%</td></tr>
        <tr><td>Moderate (e.g., cholecystectomy)</td><td>45%</td></tr>
        <tr><td>Complex (e.g., open-heart surgery)</td><td>5%</td></tr>
    </table>

    <h2>6. Post-Surgery Routing</h2>
    <h3>6.1 Post-Operative Transfers</h3>
    <ul>
        <li><strong>Simple Surgery:</strong> → General Ward</li>
        <li><strong>Moderate Surgery:</strong>
            <ul>
                <li>General Ward (70%)</li>
                <li>ICU (10%)</li>
                <li>CCU (20%)</li>
            </ul>
        </li>
        <li><strong>Complex Surgery:</strong>
            <ul>
                <li>ICU (75% non-cardiac)</li>
                <li>CCU (25% cardiac)</li>
                <li>1% require urgent reoperation</li>
                <li>10% mortality rate</li>
            </ul>
        </li>
    </ul>

    <h3>6.2 Stay Duration</h3>
    <ul>
        <li><strong>General Ward:</strong> Exponential (mean=50 hours)</li>
        <li><strong>ICU/CCU:</strong> Exponential (mean=25 hours) → General Ward</li>
    </ul>

    <h2>7. Additional Considerations</h2>
    <ul>
        <li><strong>Power Outages:</strong>
            <ul>
                <li>Once/month random occurrence</li>
                <li>Generators support: 100% ORs, 80% ICU/CCU beds</li>
            </ul>
        </li>
        <li><strong>Patient Deterioration:</strong> Ward→ICU transfers neglected</li>
        <li><strong>Discharge:</strong> After General Ward stay completion</li>
    </ul>

    <h2>8. System Flow Summary</h2>
    <ul>
        <li><strong>Elective Path:</strong><br>
            Pre-Operative → Lab → Pre-Operative (2 days) → OR → General Ward → Discharge</li>
        <li><strong>Urgent Path:</strong><br>
            ER → Lab → ER (triangular wait) → OR → [ICU/CCU/General Ward] → Discharge</li>
    </ul>
</body>
</html>
