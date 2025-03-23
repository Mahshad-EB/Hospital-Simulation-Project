<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hospital System Modeling and Simulation</title>
</head>
<body>
    <h1>Hospital System Problem Formulation</h1>
    
    <h2>Collaborative System Design Document</h2>
    
    <h3>1. System Overview</h3>
    <p>This document presents a comprehensive hospital system model with seven interconnected departments managing elective and urgent patients. The model addresses critical challenges in resource allocation, patient routing, and emergency scenarios through probabilistic modeling and operational optimization.</p>

    <h3>2. Departmental Capacity</h3>
    <table>
        <tr>
            <th>Department</th>
            <th>Bed Capacity</th>
        </tr>
        <tr><td>Pre-Operative Unit</td><td>25</td></tr>
        <tr><td>Emergency Room (ER)</td><td>10</td></tr>
        <tr><td>Laboratory</td><td>3</td></tr>
        <tr><td>Operating Rooms (ORs)</td><td>50</td></tr>
        <tr><td>General Ward</td><td>40</td></tr>
        <tr><td>ICU</td><td>10</td></tr>
        <tr><td>CCU</td><td>5</td></tr>
    </table>

    <h3>3. Patient Classification & Arrival Patterns</h3>
    <ul>
        <li><strong>Elective Patients (75%):</strong>
            <ul>
                <li>Poisson arrival rate: 1 patient/hour</li>
                <li>Pre-operative stay: 48 hours</li>
            </ul>
        </li>
        <li><strong>Urgent Patients (25%):</strong>
            <ul>
                <li>Poisson arrival rate: 4 patients/hour</li>
                <li>ER queue capacity: 10 patients</li>
                <li>0.5% group arrivals (2-5 patients)</li>
            </ul>
        </li>
    </ul>

    <h3>4. Diagnostic Workflow</h3>
    <ol>
        <li><strong>Administrative Processing:</strong>
            <ul>
                <li>Elective: 60 minutes pre-lab</li>
                <li>Urgent: 10 minutes pre-lab</li>
            </ul>
        </li>
        <li><strong>Laboratory Testing:</strong>
            <ul>
                <li>Duration: Uniform(28-32 minutes)</li>
                <li>Priority: Urgent > Elective</li>
            </ul>
        </li>
    </ol>

    <h3>5. Surgical Operations</h3>
    <ul>
        <li><strong>OR Protocols:</strong>
            <ul>
                <li>10-minute setup between surgeries</li>
                <li>Urgent patient prioritization</li>
            </ul>
        </li>
        <li><strong>Surgery Distribution:</strong>
            <table>
                <tr><th>Type</th><th>Probability</th></tr>
                <tr><td>Simple</td><td>50%</td></tr>
                <tr><td>Moderate</td><td>45%</td></tr>
                <tr><td>Complex</td><td>5%</td></tr>
            </table>
        </li>
    </ul>

    <h3>6. Post-Operative Care</h3>
    <ol>
        <li><strong>Patient Routing:</strong>
            <ul>
                <li>Simple Cases → General Ward</li>
                <li>Moderate Cases: 70% GW, 20% CCU, 10% ICU</li>
                <li>Complex Cases: 75% ICU, 25% CCU</li>
            </ul>
        </li>
        <li><strong>Care Duration:</strong>
            <ul>
                <li>General Ward: Exp(50h)</li>
                <li>ICU/CCU: Exp(25h)</li>
            </ul>
        </li>
    </ol>

    <h3>7. Emergency Protocols</h3>
    <ul>
        <li><strong>Power Outage Response:</strong>
            <ul>
                <li>Full OR generator support</li>
                <li>80% ICU/CCU backup capacity</li>
            </ul>
        </li>
        <li><strong>Critical Care:</strong>
            <ul>
                <li>1% complication rate requiring reoperation</li>
                <li>10% surgical mortality rate</li>
            </ul>
        </li>
    </ul>

    <h3>8. System Validation Challenges</h3>
    <ol>
        <li>Pre-Operative unit capacity mismatch</li>
        <li>ICU/CCU bed shortage risks</li>
        <li>General Ward overflow potential</li>
        <li>Group arrival surge management</li>
    </ol>
</body>
</html>
