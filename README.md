<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hospital Simulation System: Patient Flow and Resource Management</title>
</head>
<body>
    <h1>Hospital Simulation System: Patient Flow and Resource Management</h1>
    
    <!-- General Description -->
    <h2>System Overview</h2>
    <p>This hospital simulation model was collaboratively developed with a classmate for a healthcare operations management course. The system represents a 7-department hospital with complex patient flows and resource constraints. Key aspects include patient prioritization, surgical workflows, and emergency response mechanisms.</p>

    <!-- Department Structure -->
    <h2>Hospital Departments & Bed Capacity</h2>
    <table>
        <tr>
            <th>Department</th>
            <th>Beds</th>
        </tr>
        <tr><td>Pre-Operative Unit</td><td>25</td></tr>
        <tr><td>Emergency Room (ER)</td><td>10</td></tr>
        <tr><td>Laboratory</td><td>3</td></tr>
        <tr><td>Operating Rooms (OR)</td><td>50</td></tr>
        <tr><td>General Ward</td><td>40</td></tr>
        <tr><td>ICU</td><td>10</td></tr>
        <tr><td>CCU</td><td>5</td></tr>
    </table>

    <!-- Patient Classification -->
    <h2>Patient Types & Arrival Process</h2>
    <h3>Classification Probabilities</h3>
    <ul>
        <li>Elective Patients: 75% (Poisson λ=1/hour)</li>
        <li>Urgent Patients: 25% (Poisson λ=4/hour)</li>
    </ul>

    <h3>Special Arrival Cases</h3>
    <ul>
        <li>Group Arrivals (0.5% of urgent patients):
            <ul>
                <li>Group size: Uniform(2-5)</li>
                <li>ER queue capacity: 10 patients</li>
            </ul>
        </li>
    </ul>

    <!-- Testing & Preparation Process -->
    <h2>Pre-Operative Process</h2>
    <h3>Administrative Waiting</h3>
    <ul>
        <li>Elective: 60 minutes pre-lab</li>
        <li>Urgent: 10 minutes pre-lab</li>
    </ul>

    <h3>Laboratory Workflow</h3>
    <ul>
        <li>Testing time: Uniform(28-32 minutes)</li>
        <li>Priority: Urgent > Elective</li>
    </ul>

    <!-- Surgical Process -->
    <h2>Surgical Operations</h2>
    <h3>Surgery Types Distribution</h3>
    <table>
        <tr><th>Type</th><th>Probability</th></tr>
        <tr><td>Simple</td><td>50%</td></tr>
        <tr><td>Moderate</td><td>45%</td></tr>
        <tr><td>Complex</td><td>5%</td></tr>
    </table>

    <h3>OR Management</h3>
    <ul>
        <li>Setup time: 10 minutes between surgeries</li>
        <li>Prioritization: Urgent > Elective</li>
    </ul>

    <!-- Post-Operative Care -->
    <h2>Post-Surgical Pathways</h2>
    <h3>Patient Routing</h3>
    <ul>
        <li>Simple Surgery → General Ward
            <ul><li>Stay time: Exponential(λ=50)</li></ul>
        </li>
        <li>Moderate Surgery:
            <ul>
                <li>General Ward (70%)</li>
                <li>ICU (10%)</li>
                <li>CCU (20%)</li>
            </ul>
        </li>
        <li>Complex Surgery:
            <ul>
                <li>ICU (75% non-cardiac)</li>
                <li>CCU (25% cardiac)</li>
                <li>Mortality rate: 10%</li>
            </ul>
        </li>
    </ul>

    <h3>Critical Care Transitions</h3>
    <ul>
        <li>ICU/CCU → General Ward:
            <ul><li>Exponential(λ=25) stay duration</li></ul>
        </li>
        <li>1% readmission rate for urgent reoperation</li>
    </ul>

    <!-- Special Considerations -->
    <h2>System Constraints & Exceptions</h2>
    <h3>Power Management</h3>
    <ul>
        <li>Monthly random outages</li>
        <li>Generator capacity:
            <ul>
                <li>100% OR power</li>
                <li>80% ICU/CCU beds</li>
            </ul>
        </li>
    </ul>

    <h3>Modeling Assumptions</h3>
    <ul>
        <li>No routine ward→ICU transitions</li>
        <li>Fixed medical staff allocation</li>
        <li>Instant resource reallocation</li>
    </ul>

    <!-- System Flow Visualization -->
    <h2>Patient Flow Diagram</h2>
    <p>[Visual representation placeholder showing patient pathways through departments with probability annotations]</p>

    <!-- Technical Appendix -->
    <h2>Statistical Distributions</h2>
    <table>
        <tr><th>Process</th><th>Distribution</th></tr>
        <tr><td>Urgent Pre-OR Wait</td><td>Triangular(5,75,100)</td></tr>
        <tr><td>General Ward Stay</td><td>Exponential(λ=50)</td></tr>
        <tr><td>ICU/CCU Stay</td><td>Exponential(λ=25)</td></tr>
    </table>
</body>
</html>
