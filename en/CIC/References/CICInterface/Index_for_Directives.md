# Directive messages index

| Namespace          | Message name       | Description                                             |
|--------------------|----------------|-------------------------------------------------|
| Alerts             | [`DeleteAlert`](/CIC/References/CICInterface/Alerts.md#DeleteAlert)             | Instructs your client to delete alarms or timers.                                                  |
| Alerts             | [`GetAlert`](/CIC/References/CICInterface/Alerts.md#GetAlert)                   | Instructs your client to look up alarms or timers.                                                  |
| Alerts             | [`SetAlert`](/CIC/References/CICInterface/Alerts.md#SetAlert)                   | Instructs your client to set alarms or timers.                                                  |
| AudioPlayer        | [`Play`](/CIC/References/CICInterface/AudioPlayer.md#Play)                      | Instructs your client to start playback of a specified audio stream or add it to a playback queue.                          |
| AudioPlayer        | [`StreamDeliver`](/CIC/References/CICInterface/AudioPlayer.md#StreamDeliver)    | Returns audio stream details necessary for playback. This is a response message to an [`AudioPlayer.StreamRequested`](/CIC/References/CICInterface/AudioPlayer.md#StreamRequested) event message. |
| Clova              | [`AddMemo`](/CIC/References/CICInterface/Clova.md#AddMemo)                      | Instructs your client to add new memos.                                                  |
| Clova              | [`AddReminder`](/CIC/References/CICInterface/Clova.md#AddReminder)              | Instructs your client to add new reminders.                                               |
| Clova              | [`AddSchedule`](/CIC/References/CICInterface/Clova.md#AddSchedule)              | Instructs your client to add new schedules.                                                  |
| Clova              | [`CountSchedule`](/CIC/References/CICInterface/Clova.md#CountSchedule)          | Instructs your client to count the number of schedules within a specified period.                                 |
| Clova              | [`DeleteMemo`](/CIC/References/CICInterface/Clova.md#DeleteMemo)                | Instructs your client to delete memos.                                                       |
| Clova              | [`DeleteReminder`](/CIC/References/CICInterface/Clova.md#DeleteReminder)        | Instructs your client to delete reminders.                                                    |
| Clova              | [`DeleteSchedule`](/CIC/References/CICInterface/Clova.md#DeleteSchedule)        | Instructs your client to delete schedules.                                                       |
| Clova              | [`FinishExtension`](/CIC/References/CICInterface/Clova.md#FinishExtension)      | Instructs your client to finish a specified extension.                                             |
| Clova              | [`GetMemo`](/CIC/References/CICInterface/Clova.md#GetMemo)                      | Instructs your client to look up memos.                                                       |
| Clova              | [`GetReminder`](/CIC/References/CICInterface/Clova.md#GetReminder)              | Instructs your client to look up reminders.                                                    |
| Clova              | [`GetSchedule`](/CIC/References/CICInterface/Clova.md#GetSchedule) | Instructs your client to look up schedules.                                                       |
| Clova              | [`Hello`](/CIC/References/CICInterface/Clova.md#Hello)             | Notifies your client that a downchannel connection has been established.                                       |
| Clova              | [`Help`](/CIC/References/CICInterface/Clova.md#Help)               | Instructs your client to give pre-made help.                                       |
| Clova              | [`RenderMemoList`](/CIC/References/CICInterface/Clova.md#RenderMemoList)        | Instructs your client to display a list of memos.                                                   |
| Clova              | [`RenderReminderList`](/CIC/References/CICInterface/Clova.md#RenderReminderList) | Instructs your client to display a list of reminders.                                               |
| Clova              | [`RenderTemplate`](/CIC/References/CICInterface/Clova.md#RenderTemplate)        | Instructs your client to display templates.                                                     |
| Clova              | [`RenderText`](/CIC/References/CICInterface/Clova.md#RenderText)                | Instructs your client to display text.                                                     |
| Clova              | [`StartExtension`](/CIC/References/CICInterface/Clova.md#StartExtension)        | Instructs your client to start a specified extension.                                             |
| DeviceControl      | [`BtConnect`](/CIC/References/CICInterface/DeviceControl.md#BtConnect)          | Instructs your client to connect a specified Bluetooth device.                                       |
| DeviceControl      | [`BtDisconnect`](/CIC/References/CICInterface/DeviceControl.md#BtDisconnect)    | Instructs your client to disconnect a specified Bluetooth device.                                       |
| DeviceControl      | [`BtStartPairing`](/CIC/References/CICInterface/DeviceControl.md#BtStartPairing) | Instructs your client to start a Bluetooth pairing mode.                                          |
| DeviceControl      | [`BtStopPairing`](/CIC/References/CICInterface/DeviceControl.md#BtStopPairing)   | Instructs your client to stop a Bluetooth pairing mode.                                          |
| DeviceControl      | [`Decrease`](/CIC/References/CICInterface/DeviceControl.md#Decrease)             | Instructs your client to turn down speaker volume or decrease screen brightness by a default unit.                            |
| DeviceControl      | [`Increase`](/CIC/References/CICInterface/DeviceControl.md#Increase)             | Instructs your client to turn up speaker volume or increase screen brightness by a default unit.                            |
| DeviceControl      | [`LaunchApp`](#LaunchApp)                                                | Instructs your client to launch a specified app.                                                     |
| DeviceControl      | [`OpenScreen`](/CIC/References/CICInterface/DeviceControl.md#OpenScreen)         | Instructs your client to open a setting screen.                                                     |
| DeviceControl      | [`SetValue`](/CIC/References/CICInterface/DeviceControl.md#SetValue)            | Instructs your client to set speaker volume or screen brightness to a specified value.                           |
| DeviceControl      | [`TurnOff`](/CIC/References/CICInterface/DeviceControl.md#TurnOff)               | Instructs your client to turn off or disable a specified feature or mode.                                  |
| DeviceControl      | [`TurnOn`](/CIC/References/CICInterface/DeviceControl.md#TurnOn)                 | Instructs your client to turn on or enable a specified feature or mode.                                          |
| DeviceControl      | [`UpdateDeviceState`](#UpdateDeviceState)                                | Instructs your client to update states of other client devices registered to a user account.               |
| PlaybackController | [`Mute`](/CIC/References/CICInterface/PlaybackController.md#Mute)               | Instructs your client to mute the speaker.                                                |
| PlaybackController | [`Next`](/CIC/References/CICInterface/PlaybackController.md#Next)               | Instructs your client to start playback of a next audio stream in a playback queue.                               |
| PlaybackController | [`Pause`](/CIC/References/CICInterface/PlaybackController.md#Pause)             | Instructs your client to pause playback of a current audio stream.                                    |
| PlaybackController | [`Previous`](/CIC/References/CICInterface/PlaybackController.md#Previous)       | Instructs your client to start playback of a previous audio stream in a playback queue.                              |
| PlaybackController | [`Resume`](/CIC/References/CICInterface/PlaybackController.md#Resume)           | Instructs your client to resume playback of an audio stream.                                            |
| PlaybackController | [`Stop`](/CIC/References/CICInterface/PlaybackController.md#Stop)               | Instructs your client to stop playback of an audio stream.                                            |
| PlaybackController | [`TurnOffRepeatMode`](/CIC/References/CICInterface/PlaybackController.md#TurnOffRepeatMode) | Instructs your client to turn off the single track repeat mode.                                  |
| PlaybackController | [`TurnOnRepeatMode`](/CIC/References/CICInterface/PlaybackController.md#TurnOnRepeatMode) | Instructs your client to turn on the single track repeat mode.                                    |
| PlaybackController | [`Unmute`](/CIC/References/CICInterface/PlaybackController.md#Unmute)           | Instructs your client to unmute the speaker.                                           |
| PlaybackController | [`VolumeDown`](/CIC/References/CICInterface/PlaybackController.md#VolumeDown)   | Instructs your client to turn down the speaker volume.                                                   |
| PlaybackController | [`VolumeUp`](/CIC/References/CICInterface/PlaybackController.md#VolumeUp)       | Instructs your client to turn up the speaker volume.                                                   |
| SpeechRecognizer   | [`ExpectSpeech`](/CIC/References/CICInterface/SpeechRecognizer.md#ExpectSpeech) | Instructs your client to be ready to receive speech input from a user.                                            |
| SpeechRecognizer   | [`ShowRecognizedText`](/CIC/References/APIs/SpeechRecognizer.md#ShowRecognizedText) | Returns recognition results of user speech in real time.                                |
| SpeechRecognizer   | [`StopCapture`](/CIC/References/CICInterface/SpeechRecognizer.md#StopCapture)   | Instructs your client to stop recognizing user's speech.                                            |
| SpeechSynthesizer  | [`Speak`](/CIC/References/CICInterface/SpeechSynthesizer#Speak)                 | Instructs your client to play the synthesized TTS audio file through the speaker.                                   |