# Project-1
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
function decodeCameraImage(data)
{
    var array= data;
    var length_values=array.length;
    var array2=[];

    
    for(var i=0;i<length_values-1;i++){
        
        var red=array[i];
        var green=array[i++];
        var blue=array[i++];
        var alpha=array[i++];
        
        if(red>blue){
            return true;
            array2[i]=1;
        }else
            {
                return false;
                array2[i]=0;
            }
    
    }
    var output=bin2morse(array2);
}

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
    
    ///inter space charaters
    ".-.-": "<\br>", // New Line
    "...-.-": "SK" //end of transmission
};



function bin2morse(array){
    //=========Task 3=========//    
    var i = 0;
    var x = "";
    
    for (i=0;i<array.length;i++)
    {
	   // for inter-word space (7 unit time)
	   if(array[i]== 1 && array[i+1]== 0 && array[i+2]== 0 && array[i+3]== 0 && array[i+4]== 0 && array[i+5]== 0 && array[i+6]== 0 && array[i+7]== 0 && array[i+8]== 1)
	       {
               x += "   ";
	       }
                    
	   // for inter-character space 
	   // (3 unit time)
	       else if(array[i]== 1 && array[i+1]== 0 && array[i+2]== 0 && array[i+3]== 0 && array[i+4]==1)
	           { 
		          x += " ";
	           }
	   // (4 unit time)
	           else if(array[i]== 1 && array[i+1]== 0 && array[i+2]== 0 && array[i+3]== 0 && array[i+4]==0 && array[i+5]==1)
	               { 
		              x += " ";
	               }
	   // (5 unit time)
	               else if((array[i]== 1 && array[i+1]== 0 && array[i+2]== 0 && array[i+3]== 0 && array[i+4]==0 && array[i+5]==0 && array[i+6]==1))
	                   {  
		                  x += " ";
	                   }
	   // (6 unit time)
	                       else if((array[i]== 1 && array[i+1]== 0 && array[i+2]== 0 && array[i+3]== 0 && array[i+4]==0 && array[i+5]==0 && array[i+6]==0 && array[i+7]==1))
	                           { 
		                          x += " ";
	                           }
                    
	   // for a dash
	   // (3 unit time)
	                           else if (array [i] ==0 && array [i+1] ==1 && array [i+2] ==1 && array [i+3] ==1 && array [i+4] ==0)
	                               {
		                              x += "-";
	                               }
	   // (4 unit time)
	                               else if (array [i] ==0 && array [i+1] ==1 && array [i+2] ==1 && array [i+3] ==1 && array [i+4] ==1 && array [i+5] ==0)
	                                   {
		                                  x += "-";
	                                   }
	   // (5 unit time)
	                                   else if (array [i] ==0 && array [i+1] ==1 && array [i+2] ==1 && array [i+3] ==1 && array [i+4] ==1 && array [i+5] ==1 && array [i+6] ==0)
	                                       {
		                                      x += "-";
	                                       }
	               
	   // for a dot
	                                       else if ((array[i]==0 && array[i+1]==1 && array[i+2]==0))
	                                           {
		                                          x += ".";
	                                           }
    }
    y=x.split(" ");
    morse2val(y);
}




function morse2val(y){
    
    var counter=0;
    var outputAreaRef = document.getElementById("messageField");
    while(counter<y.length){
	if (y[counter]==""){
        outputAreaRef.innerHTML+=" ";
	}else{
        var value=y[counter];
        if morseCodeSignals[value]="SK"{
            outputAreaRef.innerHTML+=".";
        }else{
		outputAreaRef.innerHTML+=morseCodeSignals[value];
        }
	}
	counter++;
    }

}

document.getElementById("restartButton").onclick = clearmsg();
function clearmsg(){
    var outputAreaRef = document.getElementById("messageField");
    outputAreaRef.innerHTML+="";
}

	
