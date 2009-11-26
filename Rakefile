LOCAL_DIR = File.dirname(__FILE__)
LOCAL_WP = "#{LOCAL_DIR}/wordpress"
LOCAL_TMP = "#{LOCAL_DIR}/tmp"

def guess_wp_version
  version_data = File.read("#{LOCAL_WP}/wp-includes/version.php")
  if version_data =~ /^\$wp_version = '(.*)';/
    $1
  end
end

namespace :local do  
  desc "Setup wordpress"
  task :setup do
    # Fetch latest wordpress
    puts "Downloading wordpress..."
    system "curl -sO http://wordpress.org/latest.tar.gz"
    puts "Unpacking wordpress..."
    system "tar zxf latest.tar.gz"
    if version = guess_wp_version
      system "mkdir -p cache"
      system "mv latest.tar.gz cache/wordpress-#{version}.tar.gz"
    end
    puts "Installed wordpress #{version}"
  end
end