# What I did
I opened the file first and searched for hints in the picture as it was full of details. Then I opened it with a text editor after seeing a hint. It was

ˇÿˇ‡ JFIF      ˇÌ 0Photoshop 3.0 8BIM     t PicoCTF    ˇ·˘http://ns.adobe.com/xap/1.0/ <?xpacket begin='Ôªø' id='W5M0MpCehiHzreSzNTczkc9d'?>
<x:xmpmeta xmlns:x='adobe:ns:meta/' x:xmptk='Image::ExifTool 10.80'>
<rdf:RDF xmlns:rdf='http://www.w3.org/1999/02/22-rdf-syntax-ns#'>

 <rdf:Description rdf:about=''
  xmlns:cc='http://creativecommons.org/ns#'>
  <cc:license rdf:resource='cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9'/>
 </rdf:Description>

 <rdf:Description rdf:about=''
  xmlns:dc='http://purl.org/dc/elements/1.1/'>
  <dc:rights>
   <rdf:Alt>
    <rdf:li xml:lang='x-default'>PicoCTF</rdf:li>
   </rdf:Alt>
  </dc:rights>
 </rdf:Description>
</rdf:RDF>
</x:xmpmeta>
                                                                                                    
                                                                                                                                                                                                        
I did not understand any of this but PicoCTF caught my eye. And the resource='' part seemed encoded. I also opened the links just out of curiosity. Using my go to decoder website i.e dcode.fr, I found out that it is base64 encoded and I got the flag after decoding it.                                                                                                    
