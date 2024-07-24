# Weighing Tradeoffs

When deciding between CONSISTENCY and AVAILABILITY, these are the main questions we should ask ourselves.

- What kind of data are we dealing with?
  - Non-sensitive and non-critical: Social media posts, comments etc.
  - Critical: Ride confirmations, payment receipts, driver arrivals
- Can we afford to have inconsistent / inaccurate data?
- Do we need the response to be immediate?
- If we need it to be consistent and reliable, e.g. critical data, then we must focus on consistency. This trade-off is usually acceptable in scenarios where accuracy is more critical than immediate response.
- If not, we can lean towards availability.

## Consistency

### PROS:

- Data is accurate and reliable.

### CONS:

- Making sure all replicas of data are latest and synced can introduce latency.
- During high traffic periods, this can cause delays as it takes longer to ensure consistency across the system.

## Availability

### PROS:

- Real time, great for time sensitive updates, enhances user experience
- User expects immediate feedback, so high availability meets this expectation.

### CONS:

- Potential Inconsistencies: By prioritizing availability, there might be instances where notifications are sent with outdated or inconsistent information.
- Data Integrity Issues: Ensuring availability might lead to data being replicated across multiple nodes without immediate consistency, potentially leading to data integrity issues. Two users booking the same ride due to delayed synchronization of booking status.

<!-- DEFINITIONS -->

## Definitions

## What does unavailable mean?

"unavailable" means that the system or service is not able to process requests and provide responses. This can be due to various reasons such as network partitions, server failures, or maintenance.

### Example (Ride Hailing)

Impact: If the notification system is unavailable, users will not receive critical updates such as ride confirmations, driver arrivals, or payment receipts. This can lead to confusion, double bookings, and a poor user experience.

## Consistency

Requirement: Before a notification is sent, the system must ensure that all data sources and services involved in generating that notification are consistent. For example, if a ride is confirmed, all databases and services must reflect the new status of the ride.

Impact: This can introduce latency because the system might need to wait for various components to synchronize, especially in a distributed environment.

## Transaction Commitment

Process: A transaction is only committed once the system verifies that all components have the latest and consistent data. This is crucial to avoid sending incorrect or conflicting notifications.

Impact: During high traffic periods, this verification process can cause delays, as it might take longer to ensure consistency across all parts of the system.

## Tradeoffs

### Latency vs. Reliability

Prioritizing consistency ensures that notifications are accurate and reliable, but at the cost of potential latency. For example, confirming a ride might take longer because the system waits for all data to be consistent before sending a notification.

### User Experience:

Users might experience slight delays in receiving notifications, but the information they receive will be correct and reliable. This trade-off is usually acceptable in scenarios where accuracy is more critical than immediate response.
