# encoding: UTF-8

require 'json'

task :default => [:dict]

task :dict do
  json_file = IO.read "♡.json"
  json_data = JSON.parse(json_file).sort
  
  kaomoji_dict = ""
  json_data.each do |item|
    kana, kaomojis = item
    if kaomojis.class == Array
      kaomojis.each do |kaomoji|
        kaomoji_dict += "ー#{kana} #T35*500 #{kaomoji}\n"
      end
    else
      kaomoji_dict += "ー#{kana} #T35*500 #{kaomojis}\n"
    end
  end
  
  IO.write("ibus__kaomoji", kaomoji_dict)
end

task :install => :dict do
  sh "mv -f ibus__kaomoji $HOME/.anthy/imported_words_default.d/ibus__kaomoji"
end
