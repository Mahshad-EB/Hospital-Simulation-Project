<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Hospital Simulation Project</title>
</head>
<body>
<h1>Hospital Simulation Project (Phase I)</h1>

<h2>Collaborative Project</h2>
<p>This project was completed as part of a group effort with one of my classmates.</p>

<h2>Overview</h2>
<p>The following content is derived from the file <strong>Phase I.pdf</strong>, which outlines the problem statement, scenario, and requirements for modeling and simulating a hospital system. The project focuses on analyzing patient flows and resource utilization within various hospital departments, with an emphasis on elective and non-elective surgery patients.</p>

<h2>Problem Statement</h2>
<p>The hospital system comprises seven main departments:</p>
<ul>
    <li>Pre-Surgery Admission Unit</li>
    <li>Emergency Room (ER)</li>
    <li>Laboratory for Pre-Surgery Tests</li>
    <li>Operating Rooms</li>
    <li>General ICU/CCU for recovery after surgery or simpler procedures</li>
    <li>Specialized ICU for patients with complex surgeries or critical conditions</li>
    <li>Cardiac CCU for heart surgery patients</li>
</ul>

<p>The resources available in the hospital, such as beds and medical equipment, are distributed across these departments as follows:</p>
<ul>
    <li>Number of beds: 25 (Pre-Surgery)</li>
    <li>10 (ER)</li>
    <li>3 (Laboratory)</li>
    <li>50 (Operating Rooms)</li>
    <li>40 (General ICU/CCU)</li>
    <li>10 (Specialized ICU)</li>
    <li>5 (Cardiac CCU)</li>
</ul>

<h3>Patient Admission</h3>
<p>Patients are admitted into the hospital based on the type of surgery required (elective or non-elective).</p>
<ul>
    <li><strong>Elective Patients:</strong> These patients are scheduled for surgery after diagnosis by their physician.</li>
    <li><strong>Non-Elective Patients:</strong> These patients require immediate surgery due to emergencies or critical conditions.</li>
</ul>

<h3>Arrival and Distribution of Patients</h3>
<ul>
    <li><strong>Elective Patients:</strong> Spend two days in the pre-surgery admission unit before surgery.</li>
    <li><strong>Non-Elective Patients:</strong> Immediately proceed to the operating room if one is available.</li>
    <li><strong>Arrival Distribution:</strong> 75% of incoming patients are elective; 25% are non-elective.</li>
    <li><strong>Poisson Arrival Rates:</strong>
        <ul>
            <li>Elective patients arrive at a rate of 1 patient/hour.</li>
            <li>Non-elective patients arrive at a rate of 4 patients/hour.</li>
        </ul>
    </li>
</ul>

<h3>Other Key Details</h3>
<ul>
    <li><strong>Emergency Patients:</strong> Group arrivals due to accidents (approximately 50% of non-elective patients arrive in groups).</li>
    <li><strong>Pre-Surgery Tests:</strong> Conducted in the laboratory (priority given to non-elective patients).</li>
    <li><strong>Operating Room Preparation Time:</strong> Triangular distribution (minimum: 75 minutes, mode: 100 minutes, maximum: 5 minutes).</li>
    <li><strong>Surgery Types:</strong>
        <ul>
            <li>Simple surgeries (e.g., appendectomy).</li>
            <li>Moderate surgeries (e.g., cholecystectomy).</li>
            <li>Complex surgeries (e.g., open-heart surgery).</li>
        </ul>
    </li>
</ul>

<h3>Post-Surgery Transition</h3>
<p>Patients are distributed into different post-surgery recovery units:</p>
<ul>
    <li><strong>Simple surgeries:</strong> General ICU.</li>
    <li><strong>Complex surgeries:</strong> Specialized ICU or Cardiac CCU.</li>
</ul>
<p>Patients may require additional care or re-surgery based on complications. In rare cases (10%), patients may pass away during surgery.</p>

<h2>Project Requirements</h2>
<ul>
    <li><strong>Static Description:</strong> Model the given scenario and describe all entities, variables, events, and interactions in detail.</li>
    <li><strong>Assumptions:</strong> Clearly list any assumptions made during the modeling and simulation process.</li>
    <li><strong>Performance Evaluation:</strong> Provide at least four metrics to evaluate system performance, explaining the importance of each.</li>
    <li><strong>Dynamic Description:</strong> Create a flowchart representing all events and transitions within the system.</li>
    <li><strong>Event Scheduling:</strong> Determine and describe the scheduling process for all events in the simulation.</li>
</ul>
</body>
</html>
