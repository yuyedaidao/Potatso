source 'https://github.com/CocoaPods/Specs.git'

platform :ios, '9.0'
use_frameworks!

def fabric
    pod 'Fabric'
    pod 'Crashlytics'
end

def library
    pod 'KissXML'
    pod 'KissXML/libxml_module'
    pod 'ICSMainFramework', :path => "./Library/ICSMainFramework/"
    pod 'MMWormhole', '~> 2.0.0'
    pod 'KeychainAccess', '~> 2.4'
end

def tunnel
    pod 'MMWormhole', '~> 2.0.0'
end

def socket
    pod 'CocoaAsyncSocket', '~> 7.4.3'
end

def model
    pod 'RealmSwift'
end

target "Potatso" do
    pod 'Aspects', :path => "./Library/Aspects/"
    pod 'Cartography', '0.7.0'
    pod 'AsyncSwift', '1.7.4'
    pod 'SwiftColor', '~> 0.3.7'
    pod 'Appirater'
    pod 'Eureka', '~> 1.6.0'
    pod 'MBProgressHUD'
    pod 'CallbackURLKit', '0.2.0'
    pod 'ICDMaterialActivityIndicatorView', '~> 0.1.0'
    pod 'Reveal-iOS-SDK', '~> 1.6.2', :configurations => ['Debug']
    pod 'ICSPullToRefresh', '0.4'
    pod 'ISO8601DateFormatter', '~> 0.8'
    pod 'Alamofire', '~> 3.0'
    pod 'ObjectMapper', '~> 1.0'
    pod 'CocoaLumberjack/Swift'
    pod 'Helpshift', '5.6.1'
    pod 'PSOperations', '~> 2.3'
    pod 'CocoaLumberjack', '2.2.0'
    pod 'LogglyLogger-CocoaLumberjack', '~> 2.0'
    tunnel
    library
    fabric
    socket
    model
end

target "PacketTunnel" do
    tunnel
    socket
end

target "PacketProcessor" do
    socket
end

target "TodayWidget" do
    pod 'Cartography', '0.7.0'
    pod 'SwiftColor', '~> 0.3.7'
    library
    socket
    model
end

target "PotatsoLibrary" do
    library
    model
end

target "PotatsoModel" do
    model
end

target "PotatsoLibraryTests" do
    library
end

post_install do |installer|
    installer.pods_project.targets.each do |target|
        target.build_configurations.each do |config|
            config.build_settings['ENABLE_BITCODE'] = 'NO'
            if target.name == "HelpShift"
                config.build_settings["OTHER_LDFLAGS"] = '$(inherited) "-ObjC"'
            end
        end
    end
end

