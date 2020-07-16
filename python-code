# datafile: contact details/data
# ext: extension of the attachment
# fromadd: sendeer's email add.
  #importing modules
import smtplib
from email.mime.multipart import MIMEMultipart
from email.mime.text import MIMEText
from email.mime.base import MIMEBase
from email import encoders

datafile = " <<file path>>" #path of contacts file

ext = input("Enter attachment extension without dot(.): ")

fromadd = input("Enter sender_email: ")

with open(datafile,'r') as f1:
    fila= f1.readlines()
    print(fila)
    for i in range(0,len(fila)):
        E=fila[i].split(" ")    #to remove space
        N=len(E)
        name=E[0:N-1]
        name = [' '.join(name[0 : len(name)])]
        Email=E[N-1]
        #email address
        toadd = Email
        
        # Preparing the Email Temp.
        
        msg = MIMEMultipart()   # for multiparting the object
        msg['FROM'] = fromadd
        msg['TO'] = toadd
        msg['SUBJECT'] ="TEST SUBJECT"
        body = "TEST BODY \n This email is send by XYZ \n Thankyou!"
        msg.attach(MIMEText(body,'plain'))

          # Filename String
        
        filename=""       #initialising str
        print(filename)
        filename=filename.lstrip("")      #on the bases of experience
        for n in range(0,len(name)):
            filename="{0} {1}".format( filename.lstrip(),name[n])
            print('%s'%str(filename))
            filename= filename.replace(" ","")


        # Setting Filepath 
        
        attachment = open(r'C:\Users\xyz\abc\attachmentfolder\{0}.{1}'.format(filename,ext),'rb')     # put 'b' with r/w to read or open the file in binary format
        p = MIMEBase('image', ext, Name=filename)
        p.set_payload((attachment).read())
        encoders.encode_base64(p)
        p.add_header('Content-Disposition','attachment; filename= %s' % filename)
        msg.attach(p)
        
        # Establishing SMTP
        
        s=smtplib.SMTP('smtp.gmail.com', 587)   #for Gmail
        s.ehlo()
        s.starttls()
        s.login(fromadd,'<Sender's email id Password>')
        text=msg.as_string()
        s.sendmail(fromadd,toadd,text)
        s.quit()
        print("Email sent!")

f1.close()
