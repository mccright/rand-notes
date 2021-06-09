# This is just a snippit to I used for learning  

```python
import requests
import socket
from requests.packages.urllib3.exceptions import ConnectionError
from requests.packages.urllib3.exceptions import MaxRetryError
from requests.packages.urllib3.exceptions import TimeoutError
from requests.packages.urllib3.exceptions import SSLError as _SSLError
from requests.packages.urllib3.exceptions import HTTPError as _HTTPError
from requests.exceptions import ConnectionError, Timeout, SSLError

# Codes from the IANA Hypertext Transfer Protocol (HTTP) Status Code Registry
# http://www.iana.org/assignments/http-status-codes/http-status-codes.xhtml
# Last checked 2021-05-05
# 
# Categories
#  1xx: Informational - Request received, continuing process
#  2xx: Success - The action was successfully received, understood, and accepted
#  3xx: Redirection - Further action must be taken in order to complete the request
#  4xx: Client Error - The request contains bad syntax or cannot be fulfilled
#  5xx: Server Error - The server failed to fulfill an apparently valid request
#
# Yes, we could get all of these using the code below, 
# but how do we decide what to do?:
# from http import HTTPStatus
# import sys
# output = ""
# for sCode in list(HTTPStatus):
#     output += '%d %s, %s' % (sCode.value, sCode.phrase, sCode.description) + '\n'
# sys.stdout.write(output.rstrip() + '\n')
url = 'https://api.notarealservertesting.com'

try:
    response = requests.get(url)

    if response.status_code == 100:
        print(str(response.status_code) + ': Continue')                      #  [RFC7231, Section 6.2.1]
    elif response.status_code == 101:
        print(str(response.status_code) + ': Switching Protocols')           #  [RFC7231, Section 6.2.2]
    elif response.status_code == 102:
        print(str(response.status_code) + ': Processing')                    #  [RFC2518]
    elif response.status_code == 103:
        print(str(response.status_code) + ': Early Hints')                   #  [RFC8297]
    # 104-199 Unassigned
    elif response.status_code == 200:
        print(str(response.status_code) + ': OK')                            #  [RFC7231, Section 6.3.1]
    elif response.status_code == 201:
        print(str(response.status_code) + ': Created')                       #  [RFC7231, Section 6.3.2]
    elif response.status_code == 202:
        print(str(response.status_code) + ': Accepted, Request accepted, processing continues off-line')                      #  [RFC7231, Section 6.3.3]
    elif response.status_code == 203:
        print(str(response.status_code) + ': Non-Authoritative Information, Request fulfilled from cache') #  [RFC7231, Section 6.3.4]
    elif response.status_code == 204:
        print(str(response.status_code) + ': No Content, Request fulfilled, nothing follows')                    #  [RFC7231, Section 6.3.5]
    elif response.status_code == 205:
        print(str(response.status_code) + ': Reset Content')                 #  [RFC7231, Section 6.3.6]
    elif response.status_code == 206:
        print(str(response.status_code) + ': Partial Content')               #  [RFC7233, Section 4.1]
    elif response.status_code == 207:
        print(str(response.status_code) + ': Multi-Status')                  #  [RFC4918]
    elif response.status_code == 208:
        print(str(response.status_code) + ': Already Reported')              #  [RFC5842]
    # 209-225 Unassigned
    elif response.status_code == 226:
        print(str(response.status_code) + ': IM Used')                       #  [RFC3229]
    ## 227-299 Unassigned
    elif response.status_code == 300:
        print(str(response.status_code) + ': Multiple Choices, Object has several resources -- see URI list')              #  [RFC7231, Section 6.4.1]
    elif response.status_code == 301:
        print(str(response.status_code) + ': Moved Permanently, Object moved permanently -- see URI list')             #  [RFC7231, Section 6.4.2]
    elif response.status_code == 302:
        print(str(response.status_code) + ': Found, Object moved temporarily -- see URI list')                         #  [RFC7231, Section 6.4.3]
    elif response.status_code == 303:
        print(str(response.status_code) + ':  See Other, Object moved -- see Method and URL list')                     #  [RFC7231, Section 6.4.4]
    elif response.status_code == 304:
        print(str(response.status_code) + ': Not Modified')                  #  [RFC7232, Section 4.1]
    elif response.status_code == 305:
        print(str(response.status_code) + ': Use Proxy')                     #  [RFC7231, Section 6.4.5]
    elif response.status_code == 306:
        print(str(response.status_code) + ': Unused')                      #  [RFC7231, Section 6.4.6]
    elif response.status_code == 307:
        print(str(response.status_code) + ': Temporary Redirect')            #  [RFC7231, Section 6.4.7]
    elif response.status_code == 308:
        print(str(response.status_code) + ': Permanent Redirect')            #  [RFC7538]
    # 309-399 Unassigned
    elif response.status_code == 400:
        print(str(response.status_code) + ': Bad Request')                   #  [RFC7231, Section 6.5.1]
    elif response.status_code == 401:
        print(str(response.status_code) + ': Unauthorized')                  #  [RFC7235, Section 3.1]
    elif response.status_code == 402:
        print(str(response.status_code) + ': Payment Required')              #  [RFC7231, Section 6.5.2]
    elif response.status_code == 403:
        print(str(response.status_code) + ': Forbidden')                     #  [RFC7231, Section 6.5.3]
    elif response.status_code == 404:
        print(str(response.status_code) + ': Not Found')                     #  [RFC7231, Section 6.5.4]
    elif response.status_code == 405:
        print(str(response.status_code) + ': Method Not Allowed')            #  [RFC7231, Section 6.5.5]
    elif response.status_code == 406:
        print(str(response.status_code) + ': Not Acceptable')                #  [RFC7231, Section 6.5.6]
    elif response.status_code == 407:
        print(str(response.status_code) + ': Proxy Authentication Required') #  [RFC7235, Section 3.2]
    elif response.status_code == 408:
        print(str(response.status_code) + ': Request Timeout')               #  [RFC7231, Section 6.5.7]
    elif response.status_code == 409:
        print(str(response.status_code) + ': Conflict')                      #  [RFC7231, Section 6.5.8]
    elif response.status_code == 410:
        print(str(response.status_code) + ': Gone')                          #  [RFC7231, Section 6.5.9]
    elif response.status_code == 411:
        print(str(response.status_code) + ': Length Required')               #  [RFC7231, Section 6.5.10]
    elif response.status_code == 412:
        print(str(response.status_code) + ': Precondition Failed')           #  [RFC7232, Section 4.2][RFC8144, Section 3.2]
    elif response.status_code == 413:
        print(str(response.status_code) + ': Payload Too Large')             #  [RFC7231, Section 6.5.11]
    elif response.status_code == 414:
        print(str(response.status_code) + ': URI Too Long')                  #  [RFC7231, Section 6.5.12]
    elif response.status_code == 415:
        print(str(response.status_code) + ': Unsupported Media Type')        #  [RFC7231, Section 6.5.13][RFC7694, Section 3]
    elif response.status_code == 416:
        print(str(response.status_code) + ': Range Not Satisfiable')         #  [RFC7233, Section 4.4]
    elif response.status_code == 417:
        print(str(response.status_code) + ': Expectation Failed')            #  [RFC7231, Section 6.5.14]
    # 418-420 Unassigned
    elif response.status_code == 421:
        print(str(response.status_code) + ': Misdirected Request')           #  [RFC7540, Section 9.1.2]
    elif response.status_code == 422:
        print(str(response.status_code) + ': Unprocessable Entity')          #  [RFC4918]
    elif response.status_code == 423:
        print(str(response.status_code) + ': Locked')                        #  [RFC4918]
    elif response.status_code == 424:
        print(str(response.status_code) + ': Failed Dependency')             #  [RFC4918]
    elif response.status_code == 425:
        print(str(response.status_code) + ': Too Early')                     #  [RFC8470]
    elif response.status_code == 426:
        print(str(response.status_code) + ': Upgrade Required')              #  [RFC7231, Section 6.5.15]
    elif response.status_code == 427:
        print(str(response.status_code) + ': Unassigned')
    elif response.status_code == 428:
        print(str(response.status_code) + ': Precondition Required')         #  [RFC6585]
    elif response.status_code == 429:
        print(str(response.status_code) + ': Too Many Requests')             #  [RFC6585]
    elif response.status_code == 430:
        print(str(response.status_code) + ': Unassigned')
    elif response.status_code == 431:
        print(str(response.status_code) + ': Request Header Fields Too Large') [RFC6585]
    # 432-450 Unassigned
    elif response.status_code == 451:
        print(str(response.status_code) + ': Unavailable For Legal Reasons') #  [RFC7725]
    # 452-499 Unassigned
    elif response.status_code == 500:
        print(str(response.status_code) + ': Internal Server Error')         #  [RFC7231, Section 6.6.1]
    elif response.status_code == 501:
        print(str(response.status_code) + ': Not Implemented')               #  [RFC7231, Section 6.6.2]
    elif response.status_code == 502:
        print(str(response.status_code) + ': Bad Gateway')                   #  [RFC7231, Section 6.6.3]
    elif response.status_code == 503:
        print(str(response.status_code) + ': Service Unavailable')           #  [RFC7231, Section 6.6.4]
    elif response.status_code == 504:
        print(str(response.status_code) + ': Gateway Timeout')               #  [RFC7231, Section 6.6.5]
    elif response.status_code == 505:
        print(str(response.status_code) + ': HTTP Version Not Supported')    #  [RFC7231, Section 6.6.6]
    elif response.status_code == 506:
        print(str(response.status_code) + ': Variant Also Negotiates')       #  [RFC2295]
    elif response.status_code == 507:
        print(str(response.status_code) + ': Insufficient Storage')          #  [RFC4918]
    elif response.status_code == 508:
        print(str(response.status_code) + ': Loop Detected')                 #  [RFC5842]
    elif response.status_code == 509:
        print(str(response.status_code) + ': Unassigned')
    elif response.status_code == 510:
        print(str(response.status_code) + ': Not Extended')                  #  [RFC2774]
    elif response.status_code == 511:
        print(str(response.status_code) + ': Network Authentication Required') # [RFC6585]
    # 512-599 Unassigned
    elif response.status_code:
        print(str(response.status_code) + ': Unknown response, there is a problem!')
    else:
        print('Unknown condition, there is a problem!')
    
# https://docs.python.org/3/library/socket.html
except OSError as msg:
    print('---------------------------------------------------------------')
    print('Reached OSError -----------------------------------------------')
    print('Something bad happened.  Hostname correct?  Network OK?')
    print('---------------------------------------------------------------')
    #raise OSError()
    
except socket.error as sockerr:
    print('---------------------------------------------------------------')
    print('socket.error --------------------------------------------------')
    print('Something bad happened.  Hostname correct?  Network OK?')
    print('---------------------------------------------------------------')
    raise ConnectionError(sockerr)

except ConnectionError as e:
    raise ConnectionError(e)

except MaxRetryError as e:
    raise ConnectionError(e)

except ConnectionError as e:
    raise ConnectionError(e)

except (_SSLError, _HTTPError) as e:
    if isinstance(e, _SSLError):
        raise SSLError(e)
    elif isinstance(e, TimeoutError):
        raise Timeout(e)
    else:
        raise Timeout('Request timed out.')

```
