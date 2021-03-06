CAESAR-CIPHER
=============
def buildCoder(shift):

    """
    Returns a dict that can apply a Caesar cipher to a letter.
    The cipher is defined by the shift value. Ignores non-letter characters
    like punctuation, numbers, and spaces. 
    shift: 0 <= int < 26
    returns: dict"""
    ###
    
    CipherDictlower = {}
    originallower = string.ascii_lowercase
    shiftedlower = originallower[shift:] + originallower[:shift]

    #print originallower
    #print shiftedlower
    
    for i in range(26):
        CipherDictlower.update({originallower[i]:shiftedlower[i]})
        
        
    CipherDictupper = {}
    originalupper = string.ascii_uppercase
    shiftedupper = originalupper[shift:] + originalupper[:shift]    
    for i in range(26):
        CipherDictupper.update({originalupper[i]:shiftedupper[i]})
    
    z = dict(CipherDictlower.items() + CipherDictupper.items())
    
    
    return z
    
    
def applyCoder(text, coder):

    """
    Applies the coder to the text. Returns the encoded text.
    text: string
    coder: dict with mappings of characters to shifted characters
    returns: text after mapping coder chars to original text
    """
    
    Newtext = ""
    
    for i in text:
        if i in coder:
            #print coder[i]
            Newtext += coder[i]
        else:
            Newtext +=i
    return Newtext 
    
def applyShift(text, shift):

    """
    Given a text, returns a new text Caesar shifted by the given shift
    offset. Lower case letters should remain lower case, upper case
    letters should remain upper case, and all other punctuation should
    stay as it is.
    text: string to apply the shift to
    shift: amount to shift the text (0 <= int < 26)
    returns: text after being shifted by specified amount.
    """
    ### 
    ### 
    
    newtext = applyCoder(text, buildCoder(shift))
    
    return newtext

def findBestShift(wordList, text):

    """
    Finds a shift key that can decrypt the encoded text.
    text: string
    returns: 0 <= int < 26
    """
    ### 

    maxwords = 0
    bestshift = 0
    validwords = 0
    for k in range(26):
        mylist = []
        newtext = applyShift(text, k)
        
        mylist += newtext.split(' ')
        
        #print mylist
        
        
        for word in mylist: 
            if isWord(wordList, word) == True:
                validwords += 1
            if validwords > maxwords:
                maxwords = validwords
                bestshift = k
    return bestshift

def decryptStory():

    """
    Using the methods you created in this problem set,
    decrypt the story given by the function getStoryString().
    Once you decrypt the message, be sure to include as a comment
    your decryption of the story.
    returns: string - story in plain text
    """
    ### 
    
    loadWords()
    getStoryString()
    
    #print findBestShift(loadWords(), getStoryString())
    #print applyShift(getStoryString(), (findBestShift(loadWords(), getStoryString())))
    
    
    return applyShift(getStoryString(), (findBestShift(loadWords(), getStoryString())))
