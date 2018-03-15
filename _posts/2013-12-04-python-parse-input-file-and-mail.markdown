---
author: guidedmissile
comments: true
date: 2013-12-04 12:10:55+00:00
layout: post
link: https://inlovewithcode.wordpress.com/2013/12/04/python-parse-input-file-and-mail/
slug: python-parse-input-file-and-mail
title: Python - Parse input file and Mail
wordpress_id: 67
categories:
- Python
---

Code is here. Please check for required python libraries.

    
    #!/bin/python
    
    import os
    import smtplib
    from email.mime.multipart import MIMEMultipart
    from email.mime.text import MIMEText
    from optparse import OptionParser
    
    # Email Configuration
    _email_to_ = 'noreplay@test.com'
    _email_sender_ = 'noreplay@test.com'
    _email_cc_     = ['securitybot@test.com'] # A List is expected
    
    def send_email(message, subject, sender, to, cc = None):
        ''' Function to send email message '''
        msg = MIMEMultipart()
        msg['Subject'] = subject
        msg['From'] = sender
        msg['To'] = to
        if cc:
            msg['Cc'] = ', '.join(cc)
            to = to + cc
        text = MIMEText(message,'html')
        text.add_header('Content-Disposition', 'inline')
        msg.attach(text)
        smtp = smtplib.SMTP('mailhost')
        smtp.sendmail(sender, to, msg.as_string())
        smtp.close()
        return msg
    
    HTML_HEADER = ' '
    HTML_FOOTER = ' '
    
    parser = OptionParser()
    parser.add_option("-f", "--filename", dest="filename",
                  help="upload one FILE", metavar="FILE")
    
    (options, args) = parser.parse_args()
    
    files = [str(options.filename)]
    
    for eachfile in files: # to checks if input is provided
        if os.path.isfile(eachfile):
            message = 'Testing,............'
            subject = 'Test Mail'
            sender = _email_sender_
            to = sender
            fp = open(eachfile,'r')
            message = fp.readlines();
            message = ''.join(message);
            message = HTML_HEADER + message + HTML_FOOTER
            fp.close;
            send_email(message, subject, sender, to)
        else:
            send_email(message, subject, sender, to)


To run this script use command as below,.

    
     bash-2.0:$python thisScript.py -f log


All the log file content will be mailed to the configured mail group.
