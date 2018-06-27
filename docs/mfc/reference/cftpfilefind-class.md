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
ms.openlocfilehash: 6ba8f6d8cf90e7523fe4497cfc3b36c3616a8f10
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956281"
---
# <a name="cftpfilefind-class"></a>Klasa CFtpFileFind
Pomoc w wyszukiwania plików internetowych serwerów FTP.  
  
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
|[CFtpFileFind::GetFileURL](#getfileurl)|Pobiera adres URL, w tym ścieżki znaleziony plik.|  
  
## <a name="remarks"></a>Uwagi  
 `CFtpFileFind` obejmuje funkcje Członkowskie, które rozpocząć wyszukiwanie, zlokalizuj plik i zwraca adres URL lub inne informacje opisowe dotyczące pliku.  
  
 Inne klasy MFC przeznaczony dla Internet i lokalny plik przeszukiwane obejmują [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) i [CFileFind](../../mfc/reference/cfilefind-class.md). Razem z `CFtpFileFind`, te klasy zapewniają bezproblemowe mechanizm klienta można znaleźć określonych plików, niezależnie od serwera protokołu lub typu pliku (komputer lokalny lub zdalny serwer). Należy zauważyć, że nie jest Brak klasy MFC do wyszukiwania na serwerach HTTP, ponieważ HTTP nie obsługuje manipulowania bezpośredniego plików wymaganych do wyszukiwania.  
  
 Aby uzyskać więcej informacji o sposobie używania `CFtpFileFind` i innych klasach WinInet, zobacz artykuł [Internet programowanie za pomocą interfejsu WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="example"></a>Przykład  
 Poniższy kod ilustruje sposób wyliczyć wszystkie pliki w bieżącym katalogu serwera FTP.  
  
 [!code-cpp[NVC_MFCWinInet#8](../../mfc/codesnippet/cpp/cftpfilefind-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFileFind](../../mfc/reference/cfilefind-class.md)  
  
 `CFtpFileFind`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxinet.h  
  
##  <a name="cftpfilefind"></a>  CFtpFileFind::CFtpFileFind  
 Ta funkcja elementu członkowskiego jest wywoływana w celu utworzenia `CFtpFileFind` obiektu.  
  
```  
explicit CFtpFileFind(
    CFtpConnection* pConnection,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>Parametry  
 *pConnection*  
 Wskaźnik do `CFtpConnection` obiektu. Połączenie FTP można uzyskać przez wywołanie metody [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection).  
  
 *dwContext*  
 Identyfikator kontekstu `CFtpFileFind` obiektu. Zobacz **uwagi** uzyskać więcej informacji dotyczących tego parametru.  
  
### <a name="remarks"></a>Uwagi  
 Wartość domyślna dla *dwContext* są wysyłane przez MFC do `CFtpFileFind` obiekt z [CInternetSession](../../mfc/reference/cinternetsession-class.md) utworzony obiekt `CFtpFileFind` obiektu. Można zastąpić domyślną ustawioną wartość wybrane identyfikator kontekstu. Identyfikator kontekstu jest zwracana do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) zapewnienie stanu dla obiektu, z którym zostanie zidentyfikowana. Zapoznaj się z artykułem [pierwsze kroki Internet: WinInet](../../mfc/wininet-basics.md) uzyskać więcej informacji o identyfikatorze kontekstu.  
  
### <a name="example"></a>Przykład  
  Zapoznaj się z przykładem w omówieniu klasy wcześniej w tym temacie.  
  
##  <a name="findfile"></a>  CFtpFileFind::FindFile  
 Wywołanie tej funkcji członkowskich można znaleźć pliku FTP.  
  
```  
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,  
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```  
  
### <a name="parameters"></a>Parametry  
 *pstrName*  
 Wskaźnik do ciągu zawierającego nazwę znajduje się w pliku. Jeśli **NULL**, wywołanie przeprowadzi wyszukiwanie symbolu wieloznacznego (*).  
  
 *wartość elementu dwFlags*  
 Flagi opisujące sposób obsługi tej sesji. Te flagi można łączyć z bitowego operatora OR (&#124;) i są następujące:  
  
-   INTERNET_FLAG_RELOAD Pobierz dane z sieci, nawet jeśli jest buforowany lokalnie. Jest to domyślna wartość flagi.  
  
-   INTERNET_FLAG_DONT_CACHE nie buforują danych lokalnie lub w żadnych bram.  
  
-   INTERNET_FLAG_RAW_DATA przesłonić domyślny, aby zwrócić dane pierwotne ( [WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740) struktur FTP).  
  
-   Zabezpiecza INTERNET_FLAG_SECURE transakcji umieszczonego z protokołu Secure Sockets Layer lub procent Ta flaga jest dotyczy tylko żądania HTTP.  
  
-   INTERNET_FLAG_EXISTING_CONNECT, jeśli to możliwe, ponowne użycie istniejących połączeń z serwerem o nowych **FindFile** żądań zamiast tworzenia nowej sesji dla każdego żądania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0. Aby uzyskać rozszerzone informacje o błędzie, wywołania funkcji Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360).  
  
### <a name="remarks"></a>Uwagi  
 Po wywołaniu **FindFile** można pobrać pierwszy plik FTP, można wywołać [FindNextFile](#findnextfile) można pobrać kolejne pliki FTP.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład wcześniej w tym temacie.  
  
##  <a name="findnextfile"></a>  CFtpFileFind::FindNextFile  
 Wywołanie tej funkcji Członkowskich, aby kontynuować wyszukiwanie plików uruchomione za pomocą wywołania [FindFile](#findfile) funkcję elementu członkowskiego.  
  
```  
virtual BOOL FindNextFile();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli ma więcej plików; zero, jeśli znaleziono plik jest ostatnim w katalogu lub wystąpił błąd. Aby uzyskać rozszerzone informacje o błędzie, wywołania funkcji Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360). Jeśli znaleziono pliku ostatniego pliku w katalogu, lub jeśli pasujących plików można znaleźć `GetLastError` funkcja zwraca ERROR_NO_MORE_FILES.  
  
### <a name="remarks"></a>Uwagi  
 Tej funkcji należy wywołać co najmniej raz, przed wywołaniem dowolnej funkcji atrybutu (patrz [CFileFind::FindNextFile](../../mfc/reference/cfilefind-class.md#findnextfile)).  
  
 `FindNextFile` opakowuje funkcję Win32 [FindNextFile](http://msdn.microsoft.com/library/windows/desktop/aa364428).  
  
### <a name="example"></a>Przykład  
  Zapoznaj się z przykładem wcześniej w tym temacie.  
  
##  <a name="getfileurl"></a>  CFtpFileFind::GetFileURL  
 Wywołanie tej funkcji Członkowskich, aby uzyskać adres URL określony plik.  
  
```  
CString GetFileURL() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Pliku i ścieżki Universal lokalizatora zasobów (URL).  
  
### <a name="remarks"></a>Uwagi  
 `GetFileURL` jest podobne do funkcji członkowskiej [CFileFind::GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath), ale zwraca adres URL w postaci `ftp://moose/dir/file.txt`.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CFileFind](../../mfc/reference/cfilefind-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)   
 [Klasa CInternetFile](../../mfc/reference/cinternetfile-class.md)   
 [Cgopherfile — klasa](../../mfc/reference/cgopherfile-class.md)   
 [Klasa CHttpFile](../../mfc/reference/chttpfile-class.md)
