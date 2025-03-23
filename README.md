<h1>Hospital System Problem Formulation</h1>
<p><em>(Collaboratively developed with a classmate)</em></p>

<h2>1. Brief Overview</h2>
<p>This document outlines a detailed hospital system model comprising seven interconnected departments. The system manages two patient categories (elective and urgent) with distinct arrival patterns, prioritization rules, and treatment pathways. Key challenges include resource allocation, patient routing under uncertainty, and handling critical scenarios like power outages.</p>

<h2>2. Hospital Departments & Bed Capacity</h2>
<table>
  <thead>
    <tr>
      <th>Department</th>
      <th>Number of Beds</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Pre-Operative Unit</td>
      <td>25</td>
    </tr>
    <tr>
      <td>Emergency Room (ER)</td>
      <td>10</td>
    </tr>
    <tr>
      <td>Laboratory</td>
      <td>3</td>
    </tr>
    <tr>
      <td>Operating Rooms (ORs)</td>
      <td>50</td>
    </tr>
    <tr>
      <td>General Ward</td>
      <td>40</td>
    </tr>
    <tr>
      <td>Intensive Care Unit (ICU)</td>
      <td>10</td>
    </tr>
    <tr>
      <td>Cardiac Care Unit (CCU)</td>
      <td>5</td>
    </tr>
  </tbody>
</table>

<h2>3. Patient Classification & Arrival Process</h2>
<h3>3.1 Patient Types</h3>
<ul>
  <li><strong>Elective Patients (75%):</strong> Scheduled in advance, admitted to the Pre-Operative Unit 2 days before surgery.</li>
  <li><strong>Urgent Patients (25%):</strong> Require immediate care, prioritized for surgery. Admitted via the ER.</li>
</ul>

<h3>3.2 Arrival Rates</h3>
<ul>
  <li><strong>Elective Patients:</strong> Poisson arrival rate of 1 patient/hour.</li>
  <li><strong>Urgent Patients:</strong> Poisson arrival rate of 4 patients/hour.</li>
  <li><strong>Group Arrivals:</strong> 0.5% of urgent patients arrive in groups of 2–5 (uniformly distributed) only if ER has capacity.</li>
  <li><strong>ER Queue Limit:</strong> Up to 10 patients can wait in ambulances for ER beds.</li>
</ul>

<h2>4. Testing Process</h2>
<h3>Administrative Wait Time:</h3>
<ul>
  <li><strong>Elective (Pre-Operative):</strong> 60 minutes before lab transfer.</li>
  <li><strong>Urgent (ER):</strong> 10 minutes before lab transfer.</li>
</ul>

<h3>Laboratory Testing:</h3>
<ul>
  <li><strong>Tests:</strong> All patients undergo tests (blood/sugar).</li>
  <li><strong>Testing Time:</strong> Uniform distribution (28–32 minutes).</li>
  <li><strong>Priority:</strong> Urgent patients take precedence over elective in the lab.</li>
</ul>

<h3>Post-Testing Routing:</h3>
<ul>
  <li><strong>Elective:</strong> Return to Pre-Operative Unit for 2 days before OR transfer.</li>
  <li><strong>Urgent:</strong> Stay in ER for a triangular-distributed time (min=5 min, mode=75 min, max=100 min) before OR transfer.</li>
</ul>

<h2>5. Surgery Process</h2>
<h3>5.1 OR Setup</h3>
<ul>
  <li><strong>Setup Time:</strong> 10 minutes after each surgery.</li>
  <li><strong>Prioritization:</strong> Urgent patients bypass elective patients for OR access.</li>
</ul>

<h3>5.2 Surgery Types & Distribution</h3>
<table>
  <thead>
    <tr>
      <th>Surgery Type</th>
      <th>Probability</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Simple (e.g., appendectomy)</td>
      <td>50%</td>
    </tr>
    <tr>
      <td>Moderate (e.g., cholecystectomy)</td>
      <td>45%</td>
    </tr>
    <tr>
      <td>Complex (e.g., open-heart surgery)</td>
      <td>5%</td>
    </tr>
  </tbody>
</table>
<p><strong>Surgery Duration:</strong> Follows type-specific distributions (historical data referenced but parameters unspecified).</p>

<h2>6. Post-Surgery Routing</h2>
<h3>6.1 Post-Operative Transfers</h3>
<ul>
  <li><strong>Simple Surgery:</strong> Directly to General Ward.</li>
  <li><strong>Moderate Surgery:</strong>
    <ul>
      <li>General Ward (70%), ICU (10%), CCU (20%).</li>
    </ul>
  </li>
  <li><strong>Complex Surgery:</strong>
    <ul>
      <li>75% to ICU (non-cardiac) or 25% to CCU (cardiac).</li>
    </ul>
  </li>
  <li><strong>Complications:</strong> 1% of ICU/CCU patients deteriorate and require urgent reoperation.</li>
  <li><strong>Mortality:</strong> 10% die during surgery; sent to morgue (outside the system).</li>
</ul>

<h3>6.2 Stay Duration</h3>
<ul>
  <li><strong>General Ward:</strong> Exponential distribution (mean = 50 hours).</li>
  <li><strong>ICU/CCU:</strong> Exponential distribution (mean = 25 hours) before transfer to General Ward.</li>
</ul>

<h2>7. Additional Considerations</h2>
<ul>
  <li><strong>Power Outages:</strong>
    <ul>
      <li>Occurs once/month at random.</li>
      <li><strong>Generators:</strong> Support all ORs but only 80% of ICU/CCU beds.</li>
    </ul>
  </li>
  <li><strong>Patient Deterioration:</strong> Minimal cases of ward-to-ICU/CCU transfers (neglected in the model).</li>
  <li><strong>Discharge:</strong> Patients leave the hospital after completing their stay in the General Ward.</li>
</ul>

<p>This model integrates probabilistic events, prioritization rules, and resource constraints to simulate real-world hospital operations. Critical parameters (e.g., surgery time distributions) can be calibrated using historical data for accuracy.</p>
