# SOURCE_URL:="https://api.weather.gov/alerts/active?area=MD,DC,VA&status=actual&code=TOR,FFW,EWW,BZW,HLS,HUA,HUW,TRA,TRW,TSY,TSA,TSW,SSW,NUW,RHW,SPW,VOW,CEM&limit=500"
# SOURCE_URL:="https://s3.amazonaws.com/media.johnkeefe.net/data/example_warnings.json"
SOURCE_URL:="https://api.weather.gov/alerts/active?status=actual&area=MD&code=TOR,TOA,TRA,TRW,TSA,TSW,WSW,WSA,SSW,SSA,SPS,SVS,SVR,SVA,HLS,HUW,HUA,HWW,HWA,FLS,FLW,FLA,FFS,FFW,FFA,EWW,CFW,CFA,BZW,SPW,RHW,NUW,TOE,LAE,LEW,HMW,FRW,EVI,EQW,CEM,CDW,VOW&limit=500"
# djb ^

all: clean download warnings

clean:
	-rm ./tmp/download.json

download:
	-mkdir tmp
	wget --continue --progress=dot:mega --waitretry=60 ${SOURCE_URL} \
		--header='accept: application/geo+json' \
		--header='User-Agent: (baltsun.com, dbelson@baltsun.com)' \
		-O tmp/download.json

warnings:
	node warnings.js

slack:
	node warnings-slack.js