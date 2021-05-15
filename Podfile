
platform :ios, '10.0'

target 'DemoAutoSign' do
  
  pod 'AFNetworking'

end

post_install do | installer |
  include_debug_xcconfig("DemoAutoSign", "debug_ignore.xcconfig")
  
  installer.pods_project.new_file("../debug_ignore.xcconfig")
end


def include_debug_xcconfig(target, file)
  target_file_path = "Pods/Target Support Files/Pods-#{target}/Pods-#{target}.debug.xcconfig"

  if File.exist? target_file_path
      target_content = File.read(target_file_path)
      include_content = "#include \"#{Dir.pwd}/#{file}\"\n" # 实测使用绝对路径可以避免偶然的Xcode异常 Bundle identifier is missing
      unless target_content.include? include_content
          target_content = include_content + target_content
          File.write(target_file_path, target_content)
      end
  end
end
