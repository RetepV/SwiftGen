platform :osx, '10.9'
use_frameworks!

raise 'Please use bundle exec to run the pod command' unless defined?(Bundler)

target 'swiftgen' do
  pod 'Commander', '~> 0.8'
  pod 'StencilSwiftKit', '~> 2.3'
  podspec :path => 'SwiftGenKit.podspec'
  pod 'Yams', '~> 0.3'

  target 'SwiftGen UnitTests' do
    inherit! :complete
  end

  target 'Templates UnitTests' do
    inherit! :complete
  end
end

target 'SwiftGenKit' do
  podspec :path => 'SwiftGenKit.podspec'

  target 'SwiftGenKit UnitTests' do
    inherit! :complete
  end
end

post_install do |installer|
  swift3_pods = %w(Stencil)
  installer.pods_project.targets.each do |target|
    target.build_configurations.each do |config|
      config.build_settings['SWIFT_VERSION'] = '3.2' if swift3_pods.include?(target.name)
    end
  end
end
