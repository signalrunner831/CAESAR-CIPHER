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
    
