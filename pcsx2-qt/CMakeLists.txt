set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)

add_executable(pcsx2-qt)

target_sources(pcsx2-qt PRIVATE
	AboutDialog.cpp
	AboutDialog.h
	AboutDialog.ui
	AutoUpdaterDialog.cpp
	AutoUpdaterDialog.h
	AutoUpdaterDialog.ui
	ColorPickerButton.cpp
	ColorPickerButton.h
	CoverDownloadDialog.cpp
	CoverDownloadDialog.h
	CoverDownloadDialog.ui
	DisplayWidget.cpp
	DisplayWidget.h
	EarlyHardwareCheck.cpp
	MainWindow.cpp
	MainWindow.h
	MainWindow.ui
	PrecompiledHeader.cpp
	PrecompiledHeader.h
	SettingWidgetBinder.h
	Themes.cpp
	Translations.cpp
	QtHost.cpp
	QtHost.h
	QtKeyCodes.cpp
	QtProgressCallback.cpp
	QtProgressCallback.h
	QtUtils.cpp
	QtUtils.h
	GameList/EmptyGameListWidget.ui
	GameList/GameListModel.cpp
	GameList/GameListModel.h
	GameList/GameListRefreshThread.cpp
	GameList/GameListRefreshThread.h
	GameList/GameListWidget.cpp
	GameList/GameListWidget.h
	Settings/AdvancedSettingsWidget.cpp
	Settings/AdvancedSettingsWidget.h
	Settings/AdvancedSettingsWidget.ui
	Settings/AudioSettingsWidget.cpp
	Settings/AudioSettingsWidget.h
	Settings/AudioSettingsWidget.ui
	Settings/BIOSSettingsWidget.cpp
	Settings/BIOSSettingsWidget.h
	Settings/BIOSSettingsWidget.ui
	Settings/ControllerBindingWidget.ui
	Settings/ControllerBindingWidget_DualShock2.ui
	Settings/ControllerBindingWidgets.cpp
	Settings/ControllerBindingWidgets.h
	Settings/ControllerLEDSettingsDialog.ui
	Settings/ControllerGlobalSettingsWidget.cpp
	Settings/ControllerGlobalSettingsWidget.h
	Settings/ControllerGlobalSettingsWidget.ui
	Settings/ControllerMacroEditWidget.ui
	Settings/ControllerMacroWidget.ui
	Settings/ControllerMouseSettingsDialog.ui
	Settings/ControllerSettingsDialog.cpp
	Settings/ControllerSettingsDialog.h
	Settings/ControllerSettingsDialog.ui
	Settings/ControllerSettingWidgetBinder.h
	Settings/CreateMemoryCardDialog.cpp
	Settings/CreateMemoryCardDialog.h
	Settings/CreateMemoryCardDialog.ui
	Settings/DebugSettingsWidget.cpp
	Settings/DebugSettingsWidget.h
	Settings/DebugSettingsWidget.ui
	Settings/EmulationSettingsWidget.cpp
	Settings/EmulationSettingsWidget.h
	Settings/EmulationSettingsWidget.ui
	Settings/FolderSettingsWidget.cpp
	Settings/FolderSettingsWidget.h
	Settings/FolderSettingsWidget.ui
	Settings/GameCheatSettingsWidget.cpp
	Settings/GameCheatSettingsWidget.h
	Settings/GameCheatSettingsWidget.ui
	Settings/GameFixSettingsWidget.cpp
	Settings/GameFixSettingsWidget.h
	Settings/GameFixSettingsWidget.ui
	Settings/GameListSettingsWidget.cpp
	Settings/GameListSettingsWidget.h
	Settings/GameListSettingsWidget.ui
	Settings/GamePatchDetailsWidget.ui
	Settings/GamePatchSettingsWidget.cpp
	Settings/GamePatchSettingsWidget.h
	Settings/GamePatchSettingsWidget.ui
	Settings/GameSummaryWidget.cpp
	Settings/GameSummaryWidget.h
	Settings/GameSummaryWidget.ui
	Settings/GraphicsSettingsWidget.cpp
	Settings/GraphicsSettingsWidget.h
	Settings/GraphicsSettingsWidget.ui
	Settings/HotkeySettingsWidget.cpp
	Settings/HotkeySettingsWidget.h
	Settings/InputBindingDialog.cpp
	Settings/InputBindingDialog.h
	Settings/InputBindingDialog.ui
	Settings/InputBindingWidget.cpp
	Settings/InputBindingWidget.h
	Settings/InterfaceSettingsWidget.cpp
	Settings/InterfaceSettingsWidget.h
	Settings/InterfaceSettingsWidget.ui
	Settings/MemoryCardConvertDialog.cpp
	Settings/MemoryCardConvertDialog.h
	Settings/MemoryCardConvertDialog.ui
	Settings/MemoryCardConvertWorker.cpp
	Settings/MemoryCardConvertWorker.h
	Settings/MemoryCardSettingsWidget.cpp
	Settings/MemoryCardSettingsWidget.h
	Settings/MemoryCardSettingsWidget.ui
	Settings/DEV9DnsHostDialog.cpp
	Settings/DEV9DnsHostDialog.h
	Settings/DEV9DnsHostDialog.ui
	Settings/DEV9SettingsWidget.cpp
	Settings/DEV9SettingsWidget.h
	Settings/DEV9SettingsWidget.ui
	Settings/DEV9UiCommon.cpp
	Settings/DEV9UiCommon.h
	Settings/HddCreateQt.cpp
	Settings/HddCreateQt.h
	Settings/PatchDetailsWidget.ui
	Settings/SettingsDialog.cpp
	Settings/SettingsDialog.h
	Settings/SettingsDialog.ui
	Settings/USBBindingWidget_DrivingForce.ui
	Settings/USBBindingWidget_GTForce.ui
	Debugger/CpuWidget.cpp
	Debugger/CpuWidget.h
	Debugger/CpuWidget.ui
	Debugger/DebuggerWindow.cpp
	Debugger/DebuggerWindow.h
	Debugger/DebuggerWindow.ui
	Debugger/DisassemblyWidget.cpp
	Debugger/DisassemblyWidget.h
	Debugger/DisassemblyWidget.ui
	Debugger/MemoryViewWidget.cpp
	Debugger/MemoryViewWidget.h
	Debugger/MemoryViewWidget.ui
	Debugger/RegisterWidget.cpp
	Debugger/RegisterWidget.h
	Debugger/RegisterWidget.ui
	Debugger/BreakpointDialog.cpp
	Debugger/BreakpointDialog.h
	Debugger/BreakpointDialog.ui
	Debugger/Models/BreakpointModel.cpp
	Debugger/Models/BreakpointModel.h
	Debugger/Models/ThreadModel.cpp
	Debugger/Models/ThreadModel.h
	Debugger/Models/StackModel.cpp
	Debugger/Models/StackModel.h
	Tools/InputRecording/NewInputRecordingDlg.cpp
	Tools/InputRecording/NewInputRecordingDlg.h
	Tools/InputRecording/NewInputRecordingDlg.ui
	Tools/InputRecording/InputRecordingViewer.cpp
	Tools/InputRecording/InputRecordingViewer.h
	Tools/InputRecording/InputRecordingViewer.ui
	resources/resources.qrc
)

if(USE_ACHIEVEMENTS)
	target_sources(pcsx2-qt PRIVATE
		Settings/AchievementLoginDialog.cpp
		Settings/AchievementLoginDialog.h
		Settings/AchievementLoginDialog.ui
		Settings/AchievementSettingsWidget.cpp
		Settings/AchievementSettingsWidget.h
		Settings/AchievementSettingsWidget.ui
	)
endif()

set(TS_FILES
	Translations/pcsx2-qt_en.ts
)

target_precompile_headers(pcsx2-qt PRIVATE PrecompiledHeader.h)

target_include_directories(pcsx2-qt PRIVATE
	${Qt6Gui_PRIVATE_INCLUDE_DIRS}
	"${CMAKE_BINARY_DIR}/common/include"
	"${CMAKE_SOURCE_DIR}/pcsx2"
	"${CMAKE_SOURCE_DIR}/pcsx2-qt"
)

target_link_libraries(pcsx2-qt PRIVATE
	PCSX2_FLAGS
	PCSX2
	Qt6::Core
	Qt6::Gui
	Qt6::Widgets
	Qt6::Network
)

if(WIN32)
	set_source_files_properties(${TS_FILES} PROPERTIES OUTPUT_LOCATION "${CMAKE_SOURCE_DIR}/bin/translations")
	qt_add_lrelease(pcsx2-qt TS_FILES ${TS_FILES})
elseif(APPLE)
	# Hopefully macdeployqt will pick these up.
	qt_add_lrelease(pcsx2-qt TS_FILES ${TS_FILES})
else()
	# TODO: Copy base translations.
	qt_add_lrelease(pcsx2-qt TS_FILES ${TS_FILES} QM_FILES_OUTPUT_VARIABLE QM_FILES)
	set(QM_OUTPUT_DIR "$<TARGET_FILE_DIR:pcsx2-qt>/translations")
	add_custom_command(TARGET pcsx2-qt POST_BUILD COMMAND "${CMAKE_COMMAND}" -E make_directory "${QM_OUTPUT_DIR}")
	foreach (QM_FILE IN LISTS QM_FILES)
		get_filename_component(QM_FILE_NAME ${QM_FILE} NAME)
		add_custom_command(TARGET pcsx2-qt POST_BUILD COMMAND "${CMAKE_COMMAND}" -E copy_if_different "${QM_FILE}" "${QM_OUTPUT_DIR}/${QM_FILE_NAME}")
	endforeach()
endif()


# Currently, 7z is only needed for the Windows updater.
if(WIN32)
	target_link_libraries(pcsx2-qt PRIVATE
		LZMA::LZMA
	)
endif()

setup_main_executable(pcsx2-qt)
