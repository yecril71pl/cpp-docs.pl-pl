---
title: Klasa CFtpFileFind | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFtpFileFind
- AFXINET/CFtpFileFind
- AFXINET/CFtpFileFind::CFtpFileFind
- AFXINET/CFtpFileFind::FindFile
- AFXINET/CFtpFileFind::FindNextFile
- AFXINET/CFtpFileFind::GetFileURL
dev_langs:
- C++
helpviewer_keywords:
- CFtpFileFind [MFC], CFtpFileFind
- CFtpFileFind [MFC], FindFile
- CFtpFileFind [MFC], FindNextFile
- CFtpFileFind [MFC], GetFileURL
ms.assetid: 9667cf01-657f-4b11-b9db-f11e5a7b4e4c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 795261da81fbe8082e279bc3830f004d845e1ea7
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43196939"
---
# <a name="cftpfilefind-class"></a>Klasa CFtpFileFind
Pomoc Internetowych plikach wyszukiwania serwerów FTP.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CFtpFileFind : public CFileFind  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFtpFileFind::CFtpFileFind](#cftpfilefind)|Konstruuje `CFtpFileFind` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFtpFileFind::FindFile](#findfile)|Umożliwia znalezienie pliku na serwerze FTP.|  
|[CFtpFileFind::FindNextFile](#findnextfile)|Kontynuuje wyszukiwanie plików z poprzedniego wywołania [FindFile](#findfile).|  
|[CFtpFileFind::GetFileURL](#getfileurl)|Pobiera adres URL, w tym ścieżki pliku, znaleziono.|  
  
## <a name="remarks"></a>Uwagi  
 `CFtpFileFind` obejmuje funkcje Członkowskie, które rozpocząć wyszukiwanie, zlokalizuj plik i zwrócić adres URL lub inne opisowe informacje o pliku.  
  
 Inne klasy MFC, przeznaczony dla Internetu i plik lokalny przeszukiwane [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) i [CFileFind](../../mfc/reference/cfilefind-class.md). Wraz z `CFtpFileFind`, te klasy oferują bezproblemowe mechanizm dla klienta znaleźć określone pliki, niezależnie od tego, serwer protokołu lub typu pliku (komputer lokalny lub zdalny serwer). Zwróć uwagę, że żadna z klas MFC do wyszukiwania na serwerach HTTP, ponieważ HTTP nie obsługuje manipulowania bezpośrednie plików wymaganych do wyszukiwania.  
  
 Aby uzyskać więcej informacji o sposobie używania `CFtpFileFind` i innych klasach WinInet, zapoznaj się z artykułem [Internet programowanie za pomocą interfejsu WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="example"></a>Przykład  
 Poniższy kod pokazuje, jak wyliczyć wszystkie pliki w bieżącym katalogu serwera FTP.  
  
 [!code-cpp[NVC_MFCWinInet#8](../../mfc/codesnippet/cpp/cftpfilefind-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFileFind](../../mfc/reference/cfilefind-class.md)  
  
 `CFtpFileFind`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxinet.h  
  
##  <a name="cftpfilefind"></a>  CFtpFileFind::CFtpFileFind  
 Ta funkcja członkowska jest wywoływana, aby skonstruować `CFtpFileFind` obiektu.  
  
```  
explicit CFtpFileFind(
    CFtpConnection* pConnection,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>Parametry  
 *pConnection*  
 Wskaźnik do `CFtpConnection` obiektu. Połączenie FTP można uzyskać wywołując [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection).  
  
 *dwContext*  
 Identyfikator kontekstu `CFtpFileFind` obiektu. Zobacz **uwagi** uzyskać więcej informacji dotyczących tego parametru.  
  
### <a name="remarks"></a>Uwagi  
 Wartością domyślną dla *dwContext* są wysyłane przez MFC, aby `CFtpFileFind` obiektu z [CInternetSession](../../mfc/reference/cinternetsession-class.md) utworzony obiekt `CFtpFileFind` obiektu. Można zastąpić domyślne, aby ustawić identyfikator kontekstu do wybranej wartości. Identyfikator kontekstu jest zwracana do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) zapewnienie stanu dla obiektu, z którą jest identyfikowany. Zapoznaj się z artykułem [Internet pierwszych kroków: WinInet](../../mfc/wininet-basics.md) uzyskać więcej informacji o identyfikatorze kontekstu.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład w omówieniu klasy we wcześniejszej części tego tematu.  
  
##  <a name="findfile"></a>  CFtpFileFind::FindFile  
 Wywołaj tę funkcję elementu członkowskiego, aby znaleźć plik FTP.  
  
```  
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,  
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```  
  
### <a name="parameters"></a>Parametry  
 *pstrName*  
 Wskaźnik do ciągu zawierającego nazwę pliku, aby znaleźć. Jeśli jest to ma wartość NULL, wywołanie zostanie przeprowadzone wyszukiwanie symbolu wieloznacznego (*).  
  
 *Flagidw*  
 Flagi opisujące sposób obsługi tej sesji. Te flagi można łączyć przy użyciu bitowego operatora OR (&#124;) i są następujące:  
  
-   INTERNET_FLAG_RELOAD uzyskać danych z sieci, nawet jeśli jest ona buforowana lokalnie. Jest to flaga domyślna.  
  
-   INTERNET_FLAG_DONT_CACHE nie buforują dane, lokalnie lub w żadnych bram.  
  
-   INTERNET_FLAG_RAW_DATA zastąpić to ustawienie domyślne, aby zwrócić dane pierwotne ( [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa) struktur dla połączenia FTP).  
  
-   Zabezpiecza INTERNET_FLAG_SECURE transakcji na potrzeby przesyłu przy użyciu protokołu Secure Sockets Layer lub procent Ta flaga ma zastosowanie tylko żądania HTTP.  
  
-   INTERNET_FLAG_EXISTING_CONNECT, jeśli jest to możliwe, ponowne używanie istniejących połączeń z serwerem dla nowych `FindFile` żądania zamiast tworzenia nowej sesji dla każdego żądania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać funkcję Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360).  
  
### <a name="remarks"></a>Uwagi  
 Po wywołaniu `FindFile` można pobrać pierwszego pliku FTP, można wywołać [FindNextFile](#findnextfile) pobieranie kolejnych plików FTP.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład wcześniej w tym temacie.  
  
##  <a name="findnextfile"></a>  CFtpFileFind::FindNextFile  
 Wywołaj tę funkcję elementu członkowskiego, aby kontynuować wyszukiwanie plików, uruchomione przy użyciu wywołania do [FindFile](#findfile) funkcja elementu członkowskiego.  
  
```  
virtual BOOL FindNextFile();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli istnieje więcej plików; zero, jeśli znaleziono pliku jest ostatni z nich w katalogu lub jeśli wystąpił błąd. Aby uzyskać rozszerzone informacje o błędzie, należy wywołać funkcję Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360). Jeśli znaleziono pliku ostatniego pliku w katalogu lub jeśli nie pasujących plików można znaleźć `GetLastError` :: gettotalsize() zwróciło ERROR_NO_MORE_FILES.  
  
### <a name="remarks"></a>Uwagi  
 Musisz wywołać tę funkcję, co najmniej raz przed wywołaniem dowolnej funkcji atrybut (zobacz [CFileFind::FindNextFile](../../mfc/reference/cfilefind-class.md#findnextfile)).  
  
 `FindNextFile` opakowuje funkcję Win32 [FindNextFile](/windows/desktop/api/fileapi/nf-fileapi-findnextfilea).  
  
### <a name="example"></a>Przykład  
  Zobacz przykład we wcześniejszej części tego tematu.  
  
##  <a name="getfileurl"></a>  CFtpFileFind::GetFileURL  
 Wywołaj tę funkcję elementu członkowskiego, aby uzyskać adres URL określony plik.  
  
```  
CString GetFileURL() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Pliku i ścieżka uniwersalnych lokalizatorów zasobów (URL).  
  
### <a name="remarks"></a>Uwagi  
 `GetFileURL` jest podobna do funkcji składowej [CFileFind::GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath), chyba że zwraca adres URL w postaci `ftp://moose/dir/file.txt`.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CFileFind](../../mfc/reference/cfilefind-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)   
 [Klasa CInternetFile](../../mfc/reference/cinternetfile-class.md)   
 [Cgopherfile — klasa](../../mfc/reference/cgopherfile-class.md)   
 [Klasa CHttpFile](../../mfc/reference/chttpfile-class.md)
