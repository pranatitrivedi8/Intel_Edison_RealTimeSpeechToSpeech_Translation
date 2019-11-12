"use strict" ;

var mraa = require('mraa');	// Import the MRAA module


//Mini Breakout
var red = new mraa.Gpio(31);// Set up a digital input/output on MRAA pin 31 (GP44)
var green = new mraa.Gpio(32);// Set up a digital input/output on MRAA pin 32 (GP46)
var blue = new mraa.Gpio(33);// Set up a digital input/output on MRAA pin 33 (GP48)

red.dir(mraa.DIR_IN);
green.dir(mraa.DIR_IN);
blue.dir(mraa.DIR_IN);


// load required modules
var async = require('async'); // helps control asynchronous flow
var path = require('path'); // utility for handling file paths
var exec = require('child_process').exec; // runs a command in a shell and buffers the output
var spawn = require('child_process').spawn; // launches a child process
var request = require('request'); // http request client
var watson = require('watson-developer-cloud'); // IBM Watson services client
//var five = require('johnny-five'); // robotics programming framework
//var Edison = require('edison-io'); // edison IO library
var numify = require('numstr').numify; // english number utility
// globals

var working = false; // keeps track of if we are already working on a command

var drsfun8 = 1;

// initialize watson text-to-speech service
var textToSpeech = watson.text_to_speech({
 username: "a2f02629-3c88-493d-a42b-dc9eae802e3c",
 password: 'ADMZwHFEEYJm',
 version: 'v1'
});


// initialize watson speech-to-text service
var speechToText = watson.speech_to_text({
username: "8d985f9b-f72a-4e9b-98ab-e762ea6762ac",
password: 'Ip3ALSXlbZsH',
version: 'v1'
});

var http = require('http');

// When you have your own Client ID and secret, put down their values here:
var clientId = "drs.patel1997@gmail.com";
var clientSecret = "bf6ce9ec04ca4496aa06e0a70e0b1049";

// accepts a string and reads it aloud
function tts (text, cb) {
// build tts parameters
	var params = {
		text: text,
		accept: 'audio/wav'
	};
	// create gtstreamer child process to play audio
	// "fdsrc fd=0" says file to play will be on stdin
	// "wavparse" processes the file as audio/wav
	// "pulsesink" sends the audio to the default pulse audio sink device
	var gst = exec('gst-launch-1.0 fdsrc fd=0 ! wavparse ! pulsesink', function (err) {
		if (err) { return cb(err); }
		cb();

	});

	// use watson and pipe the text-to-speech results directly to gst
	textToSpeech.synthesize(params).pipe(gst.stdin);
}

// listens for audio then returns text
function stt (cb) {
	var duration = 5000;
	var text = '';

	console.log('listening for %s ms ...', duration);


	// create an arecord child process to record audio
	var arecord = spawn('arecord', ['-D', 'hw:2,0', '-t', 'wav', '-f', 'S16_LE']);
	// build stt params using the stdout of arecord as the audio source
	var params = {
		audio: arecord.stdout,
		content_type: 'audio/wav',
		continuous: true // listen for audio the full 5 seconds
	};
	// use watson to get answer text
	speechToText.recognize(params, function (err, res) {
	if (err) { return cb(err); }
	text = '';
	try {
		text = res.results[0].alternatives[0].transcript;
	} catch (e) { }
		console.log('you said: "%s"', text);
		cb(null, text.trim());
	});

	// record for duration then kill the child process
	setTimeout(function () {
		arecord.kill('SIGINT');
	}, duration);
}

// plays a local wav file
function playWav (file, cb) {
//var filePath = path.resolve(__dirname, file);
	var filePath = path.resolve(__dirname, file);
// create gtstreamer child process to play audio
// "filesrc location=" says use a file at the location as the src
// "wavparse" processes the file as audio/wav
// "volume" sets the output volume, accepts value 0 - 1
// "pulsesink" sends the audio to the default pulse audio sink device
	exec('gst-launch-1.0 filesrc location=' + filePath + ' ! wavparse ! volume volume=0.75 ! pulsesink', function (err) {
		return cb(err);
	});
}


	main();


// when the board is ready, listen for a button press



// main function
function main() {
	if (working) { return; }
	working = true;
	drsfun8=1;


	periodicActivity();
	function periodicActivity() //
	{
			console.log('                                                  ' );
			console.log('                                                  ' );
			console.log('                                                  ' );
			console.log('                                                  ' );
			console.log('                                                  ' );

	// Perform a quick connection to the IMAP server and look for unread emails
		if(drsfun8==1){
				console.log('English to Spanish  Translation - Speech to Speech' );
			}

			if(drsfun8==2){
				console.log('Spanish to English  Translation - Speech to Speech' );
			}

			if(drsfun8==3){
				console.log("Hindi to English    Translation - Speech to Speech");
			}

			if(drsfun8==4){
				console.log('English to Hindi    Translation - Speech to Text  ' );
			}

			if(drsfun8==5){
				console.log('English to Kannad   Translation - Speech to Text  ' );
			}

			if(drsfun8==6){
				console.log('English to Gujarati Translation - Speech to Text  ' );
			}

			if(drsfun8==7){
				console.log('Language Acquistion Device                        ' );
			}

			if(drsfun8==8){
				console.log('Music Player - Hindi Aashayea.....                ' );
			 }

			if(drsfun8==9){
				console.log('Music Player - ChillingMusic .....                ' );
			 }


			console.log('Waiting for key press, blue - Down, green - Enter, red- Up ' );

			while (blue.read()==1 && green.read()==1 && red.read()==1)	{
			}
			console.log('Key Pressed....                                      ' );

			if (blue.read()==0)	{
				drsfun8++;
				if(drsfun8>9)
					drsfun8 = 1;
				setTimeout(periodicActivity,1000);
			}

			if (red.read()==0)	{
				drsfun8--;
				if(drsfun8<1)
					drsfun8 = 9;
				setTimeout(periodicActivity, 1000);
			}

			if (green.read()==0)	{

				if(drsfun8>=1 && drsfun8<=3){
					async.waterfall([listen,text_translation,speak], finish);
				}


				if(drsfun8>=4 && drsfun8<=6){
					async.waterfall([listen,text_translation], finish);
				}

				if(drsfun8==7){
					async.waterfall([listen,search,speak], finish);
				}


				if(drsfun8==8){
					console.log('Playing Song1 ...' );
					async.waterfall([async.apply(playWav, 'song.wav')], finish);
				}

				if(drsfun8==9){
					console.log('Playing Song2 ...' );
					async.waterfall([async.apply(playWav, 'ChillingMusic.wav')], finish);
				}

				// Wait for 30 seconds before checking for emails again
				setTimeout(periodicActivity, 30000);
			}


	}


}

// listen for the audio input
function listen (cb) {
	stt(cb);
}

// perform a search using the duckduckgo instant answer api
function search (q, cb) {
	if (!q) {
		return cb(null, 'I\'m sorry I didn\'t hear you.');
	}
	// blick the led every 100 ms
	//led.blink(100);
	// run the query through numify for better support of calculations in duckduckgo
	q = numify(q);
	console.log('searching for: %s', q);

	var requestOptions = {
		url: 'https://api.duckduckgo.com/',
		accept: 'application/json',
		qs: {
		q: q,
		format: 'json',
		no_html: 1,
		skip_disambig: 1
		}
	};
	request(requestOptions, function (err, res, body) {
		if (err) { return cb(err); }
		var result = JSON.parse(body);
		var text = 'I\'m sorry, I was unable to find any information on ' + q; // default response
		//var text =  ; // default response
		if (result.Answer) {
			text = result.Answer;
		} else if (result.Definition) {
			text = result.Definition;
		} else if (result.AbstractText) {
			text = result.AbstractText;
		}
		cb(null, text);
	});
}

function finish (err) {
	if (err) {
		tts('Oops, something went wrong and I was unable to complete your request.');
		console.log(err);
	}
	working = false;
}

// read the search results
function speak (text, cb) {
	if (!text) { return cb(); }
	tts(text, cb);
}




function text_translation (text, cb) {
if(drsfun8==1){
	var fromLang = "en";
	var toLang = "es";
}
if(drsfun8==2){
	var fromLang = "es";
	var toLang = "en";
}
	if(drsfun8==3){
	var fromLang = "hi";
	var toLang = "en";
}
if(drsfun8==4){
	var fromLang = "en";
	var toLang = "hi";
}
if(drsfun8==5){
	var fromLang = "en";
	var toLang = "kn";
}
if(drsfun8==6){
	var fromLang = "en";
	var toLang = "gu";
}

var jsonPayload = JSON.stringify({
    fromLang: fromLang,
    toLang: toLang,
    text: text
});


// TODO: Specify your translation requirements here:


var options = {
    hostname: "api.whatsmate.net",
    port: 80,
    path: "/v1/translation/translate",
    method: "POST",
    headers: {
        "Content-Type": "application/json",
        "X-WM-CLIENT-ID": clientId,
        "X-WM-CLIENT-SECRET": clientSecret,
        "Content-Length": Buffer.byteLength(jsonPayload)
    }
};

var request = new http.ClientRequest(options);
request.end(jsonPayload);

	request.on('response', function (response) {
		console.log('Status code: ' + response.statusCode);
		response.setEncoding('utf8');
		response.on('data', function (chunk) {
			console.log('Translated text:');
			console.log(chunk);


			text = chunk;
			cb(null, chunk);	//enable for Hindi not working
		});
	});

}
