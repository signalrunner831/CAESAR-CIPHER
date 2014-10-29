CAESAR-CIPHER
=============
def buildCoder(shift):

    """
    Returns a dict that can apply a Caesar cipher to a letter.
    The cipher is defined by the shift value. Ignores non-letter characters
    like punctuation, numbers, and spaces. 
    shift: 0 <= int < 26
    returns: dict"""
    ### TODO 
    
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
    ### TODO.
    ### HINT: This is a wrapper function.
    
    newtext = applyCoder(text, buildCoder(shift))
    
    return newtext
