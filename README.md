# Tatanexon-car-ev-model
% Define the duration of the fleet BEV drive cycle in seconds
duration = 1800; % 30 minutes
% Create a time vector for the drive cycle
time = (0:1:duration)';
% Generate a synthetic speed profile for the fleet BEV drive cycle
% This profile includes variations in speed
speed_profile = 10 + 5 * sin(2 * pi * time / 300) + 2 * randn(size(time));
% Generate a synthetic distance profile based on speed
distance_profile = cumtrapz(time, speed_profile);
% Create a table to store the fleet BEV drive cycle data
fleetBEVData = table(time, speed_profile, distance_profile);
% Specify the filename for the XLSX file
filename = 'fleet_bev_drive_cycle_data.xlsx';
% Save the table to an XLSX file
writetable(fleetBEVData, filename);
Unable to save the workbook to file 'C:\fleet_bev_drive_cycle_data.xlsx'. Check that write permissions are available, there is sufficient disk space, and the file can be written to or created.
% Plot the fleet BEV drive cycle data
figure;
subplot(2, 1, 1);
plot(time, speed_profile);
xlabel('Time (s)');
ylabel('Speed (m/s)');
title('Fleet BEV Drive Cycle - Speed Profile');
subplot(2, 1, 2);
plot(time, distance_profile);
xlabel('Time (s)');
ylabel('Distance (m)');
title('Fleet BEV Drive Cycle - Distance Profile');
% Display a message indicating that the data has been saved
fprintf('Fleet BEV drive cycle data has been saved to %s\n', filename);
