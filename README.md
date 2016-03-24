# Project-1

//Type the code here
//sanjey- ok la got the file
// good good
//got it too -adrian


/*
 * Morse Code receiver app information:
 *
 * Function: messageFinished(): stops the capturing process
 *
 *     You can call this function to let the app know that the 
 *     end-of-transmission signal has been received.
 *
 * -------------------------------------------------------
 *
 * ID: messageField: id of the message text area
 *
 *     This will be a textarea element where you can display
 *     the recieved message for the user.
 * 
 * -------------------------------------------------------
 *
 * ID: restartButton: id of the Restart button
 *
 *     This is a button element.  When clicked this should 
 *     cause your app to reset its state and begin recieving
 *     a new message.
 *
 */


// ADD YOUR ADDITIONAL FUNCTIONS AND GLOBAL VARIABLES HERE

// Morse code signals
var morseCodeSignals = {

    // alphabets
    ".-": "a",
    "-...": "b",
    "-.-.": "c",
    "-..": "d",
    ".": "e",
    "..-.": "f",
    "--.": "g",
    "....": "h",
    "..": "i",
    ".---": "j",
    "-.-": "k",
    ".-..": "l",
    "--": "m",
    "-.": "n",
    "---": "o",
    ".--.": "p",
    "--.-": "q",
    ".-.": "r",
    "...": "s",
    "-": "t",
    "..-": "u",
    "...-": "v",
    ".--": "w",
    "-..-": "x",
    "-.--": "y",
    "--..": "z",
    
    // numbers
    "-----": "0",
    ".----": "1",
    "..---": "2",
    "...--": "3",
    "....-": "4",
    ".....": "5",
    "-....": "6",
    "--...": "7",
    "---..": "8",
    "----.": "9",
    
    // symbols
    "-.--.": "(",
    "-.--.-": ")",
    "........-..-": "$",
    ".----.": "\"",
    "-..-.": "/",
    ".-.-.": "+",
    "---...": ":",
    ".-.-.-": ".",
    "--..--": ",",
    "..--..": "?",
    "-....-": "-",
    ".--.-.": "@",
    "-...-": "=",
    "..--.-..--.-": "_",
    "---.---.": "!",
    
    inter space charaters
    ".-.-": "\n", \\ New Line
    "...-.-": "SK" \\end of transmission
};


/*
 * This function is called once per unit of time with camera image data.
 * 
 * Input : Image Data. An array of integers representing a sequence of pixels.
 *         Each pixel is representing by four consecutive integer values for 
 *         the 'red', 'green', 'blue' and 'alpha' values.  See the assignment
 *         instructions for more details.
 * Output: You should return a boolean denoting whether or not the image is 
 *         an 'on' (red) signal.
 */
function decodeCameraImage(data) {
    // ADD YOUR CODE HERE

    return false;
}

var array = [0,1,0,1,1,1,0,0,0,0,0,0,0,1,1,1,0,1,0,1,0,1,0,0,0,1,0,1,1,1,0,0,0,1,1,1,0,1,0,1,1,1,0,1,0,0,0,0,0,0,0,0,1,1,1,0,1,1,1,0,1,0];
                var i = 0;
                var x = "";
                
                for (i=0;i<array.length;i++)
                {
                    // for inter-word space
	               if((array[i]== 0 && array[i+1]== 0 && array[i+2]== 0 && array[i+3]== 0 && array[i+4]== 0 && array[i+5]== 0 && array[i+6]== 0))
	               {
                       x += '\t';
	               }
                    
		            // for inter-character space
	               else if((array[i]== 1 && array[i+1]== 0 && array[i+2]== 0 && array[i+3]== 0 && array[i+4]==1))
	               { 
		              x += "\xa0";
	               }
			
                    // for a dash
	               else if (array [i] ==0 && array [i+1] ==1 && array [i+2] ==1 && array [i+3] ==1)
	               {
		              x += "-";
	               }
			
                    // for a dot
	               else if ((array[i]==0 && array[i+1]==1 && array[i+2]==0))
	               {
		              x += ".";
	               }
	
                }

                console.log(x);
                

