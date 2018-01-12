---
title: Klasa CInternetFile | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CInternetFile
- AFXINET/CInternetFile
- AFXINET/CInternetFile::CInternetFile
- AFXINET/CInternetFile::Abort
- AFXINET/CInternetFile::Close
- AFXINET/CInternetFile::Flush
- AFXINET/CInternetFile::GetLength
- AFXINET/CInternetFile::Read
- AFXINET/CInternetFile::ReadString
- AFXINET/CInternetFile::Seek
- AFXINET/CInternetFile::SetReadBufferSize
- AFXINET/CInternetFile::SetWriteBufferSize
- AFXINET/CInternetFile::Write
- AFXINET/CInternetFile::WriteString
- AFXINET/CInternetFile::m_hFile
dev_langs: C++
helpviewer_keywords:
- CInternetFile [MFC], CInternetFile
- CInternetFile [MFC], Abort
- CInternetFile [MFC], Close
- CInternetFile [MFC], Flush
- CInternetFile [MFC], GetLength
- CInternetFile [MFC], Read
- CInternetFile [MFC], ReadString
- CInternetFile [MFC], Seek
- CInternetFile [MFC], SetReadBufferSize
- CInternetFile [MFC], SetWriteBufferSize
- CInternetFile [MFC], Write
- CInternetFile [MFC], WriteString
- CInternetFile [MFC], m_hFile
ms.assetid: 96935681-ee71-4a8d-9783-5abc7b3e6f10
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f1e4b05e2aceb8fb4c8a4abed0dd6038fff6cfee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cinternetfile-class"></a>Klasa CInternetFile
Umożliwia dostęp do plików w systemach zdalnych, które używają protokołów internetowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CInternetFile : public CStdioFile  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="protected-constructors"></a>Konstruktory chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CInternetFile::CInternetFile](#cinternetfile)|Konstruuje `CInternetFile` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CInternetFile::Abort](#abort)|Powoduje zamknięcie pliku, ignorując wszystkie ostrzeżenia i błędy.|  
|[CInternetFile::Close](#close)|Zamyka `CInternetFile` i zwalnia jego zasoby.|  
|[CInternetFile::Flush](#flush)|Opróżnia bufor zapisu zawartości i upewnia się, że dane w pamięci są zapisywane na komputerze docelowym.|  
|[CInternetFile::GetLength](#getlength)|Zwraca rozmiar pliku.|  
|[CInternetFile::Read](#read)|Odczytuje liczba określonych bajtów.|  
|[CInternetFile::ReadString](#readstring)|Odczytuje strumienia znaków.|  
|[CInternetFile::Seek](#seek)|Zmienia położenie wskaźnika, w której plik otwarty.|  
|[CInternetFile::SetReadBufferSize](#setreadbuffersize)|Ustawia rozmiar buforu, w którym będzie można odczytać danych.|  
|[CInternetFile::SetWriteBufferSize](#setwritebuffersize)|Ustawia rozmiar buforu, w którym będą zapisywane dane.|  
|[CInternetFile::Write](#write)|Zapisuje liczba określonych bajtów.|  
|[CInternetFile::WriteString](#writestring)|Zapisuje ciąg znaków zakończony znakiem null do pliku.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CInternetFile::operator HINTERNET](#operator_hinternet)|Operator rzutowania dojścia internetowego.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CInternetFile::m_hFile](#m_hfile)|Dojście do pliku.|  
  
## <a name="remarks"></a>Uwagi  
 Udostępnia klasę podstawową dla [CHttpFile](../../mfc/reference/chttpfile-class.md) i [cgopherfile —](../../mfc/reference/cgopherfile-class.md) klasy plików. Nigdy nie twórz `CInternetFile` obiekt bezpośrednio. Zamiast tego utworzyć przez wywołanie obiektu jednej z jej klas pochodnych [CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) lub [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest). Można również utworzyć `CInternetFile` obiektu przez wywołanie metody [CFtpConnection::OpenFile](../../mfc/reference/cftpconnection-class.md#openfile).  
  
 `CInternetFile` Funkcje Członkowskie **Otwórz**, `LockRange`, `UnlockRange`, i `Duplicate` nie są zaimplementowane w przypadku `CInternetFile`. Jeśli wywoływać te funkcje na `CInternetFile` obiektu, otrzymasz [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).  
  
 Aby dowiedzieć się więcej na temat `CInternetFile` współpracuje z innych klas MFC Internet, zapoznaj się z artykułem [Internet programowanie za pomocą interfejsu WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Cfile —](../../mfc/reference/cfile-class.md)  
  
 [CStdioFile](../../mfc/reference/cstdiofile-class.md)  
  
 `CInternetFile`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxinet.h  
  
##  <a name="abort"></a>CInternetFile::Abort  
 Zamyka pliku skojarzone z tym obiektem i sprawia, że plik jest niedostępny dla operacji odczytu lub zapisu.  
  
```  
virtual void Abort();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli plik nie został zamknięty przed niszczenie obiektu, destruktor zamyka dla Ciebie.  
  
 Podczas obsługi wyjątków, **przerwać** różni się od [Zamknij](#close) na dwa sposoby ważne. Najpierw **przerwać** funkcji nie Zgłoś wyjątek przy błędach ponieważ ignoruje ona błędów. Drugi, **przerwać** nie **ASSERT** Jeśli plik nie został otwarty lub została wcześniej zamknięta.  
  
##  <a name="cinternetfile"></a>CInternetFile::CInternetFile  
 Ta funkcja członkowska jest wywoływane, gdy `CInternetFile` tworzony jest obiekt.  
  
```  
CInternetFile(
    HINTERNET hFile,  
    LPCTSTR pstrFileName,  
    CInternetConnection* pConnection,  
    BOOL bReadMode);

 
CInternetFile(
    HINTERNET hFile,  
    HINTERNET hSession,  
    LPCTSTR pstrFileName,  
    LPCTSTR pstrServer,  
    DWORD_PTR dwContext,  
    BOOL bReadMode);
```  
  
### <a name="parameters"></a>Parametry  
 `hFile`  
 Dojście do pliku internetowych.  
  
 `pstrFileName`  
 Wskaźnik do ciąg zawierający nazwę pliku.  
  
 `pConnection`  
 Wskaźnik do [CInternetConnection](../../mfc/reference/cinternetconnection-class.md) obiektu.  
  
 *bReadMode*  
 Wskazuje, czy plik jest tylko do odczytu.  
  
 `hSession`  
 Dojście do sesji Internetu.  
  
 `pstrServer`  
 Wskaźnik do ciąg zawierający nazwę serwera.  
  
 `dwContext`  
 Identyfikator kontekstu `CInternetFile` obiektu. Zobacz [podstawy WinInet](../../mfc/wininet-basics.md) uzyskać więcej informacji o identyfikatorze kontekstu.  
  
### <a name="remarks"></a>Uwagi  
 Nigdy nie twórz `CInternetFile` obiekt bezpośrednio. Zamiast tego utworzyć przez wywołanie obiektu jednej z jej klas pochodnych [CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) lub [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest). Można również utworzyć `CInternetFile` obiektu przez wywołanie metody [CFtpConnection::OpenFile](../../mfc/reference/cftpconnection-class.md#openfile).  
  
##  <a name="close"></a>CInternetFile::Close  
 Zamyka `CInternetFile` i zwalnia jego zasobach.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli plik został otwarty do zapisu, jest niejawne wywołanie [opróżnić](#flush) aby mieć pewność, że wszystkie buforowane dane są zapisywane do hosta. Należy wywołać **Zamknij** po zakończeniu przy użyciu pliku.  
  
##  <a name="flush"></a>CInternetFile::Flush  
 Wywołanie tej funkcji Członkowskich opróżnić zawartości buforu zapisu.  
  
```  
virtual void Flush();
```  
  
### <a name="remarks"></a>Uwagi  
 Użyj `Flush` aby mieć pewność, że wszystkie dane w pamięci faktycznie został zapisany na komputerze docelowym i upewnić się, że wykonano transakcji o komputerze hosta. `Flush`obowiązuje tylko na `CInternetFile` obiektów otwarty do zapisu.  
  
##  <a name="getlength"></a>CInternetFile::GetLength  
 Zwraca rozmiar pliku.  
  
```  
virtual ULONGLONG GetLength() const;  
```  
  
##  <a name="m_hfile"></a>CInternetFile::m_hFile  
 Dojście do pliku skojarzone z tym obiektem.  
  
```  
HINTERNET m_hFile;  
```  
  
##  <a name="operator_hinternet"></a>CInternetFile::operator HINTERNET  
 Użyj tego operatora, można pobrać uchwytu systemu Windows dla bieżącej sesji Internet.  
  
```  
operator HINTERNET() const;  
```  
  
##  <a name="read"></a>CInternetFile::Read  
 Wywołanie tej funkcji Członkowskich do odczytu do danego pamięci, zaczynając od `lpvBuf`, określona liczba bajtów, `nCount`.  
  
```  
virtual UINT Read(
    void* lpBuf,  
    UINT nCount);
```  
  
### <a name="parameters"></a>Parametry  
 `lpBuf`  
 Wskaźnik do adres pamięci, aby plik, który jest do odczytu danych.  
  
 `nCount`  
 Liczba bajtów do zapisania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba bajtów przesłanych w buforze. Wartość zwracana może być mniejsza niż `nCount` czy osiągnięto koniec pliku.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja zwraca liczbę bajtów odczytanych w rzeczywistości — liczba, która może być mniejsza niż `nCount` , gdy kończy się plik. Jeśli wystąpi błąd podczas odczytywania pliku, funkcja zwraca [CInternetException](../../mfc/reference/cinternetexception-class.md) obiektu, który opisuje błąd. Należy pamiętać, że odczytu poza końcem pliku nie jest traktowane jako błąd i nie zostanie wygenerowany wyjątek.  
  
 Aby upewnić się, wszystkie dane są pobierane, aplikacja musi nadal wywołać **CInternetFile::Read** metody do momentu metoda zwraca wartość zero.  
  
##  <a name="readstring"></a>CInternetFile::ReadString  
 Wywołanie tej funkcji członkowskich można odczytać strumienia znaków, aż do znalezienia znaku nowego wiersza.  
  
```  
virtual BOOL ReadString(CString& rString);

 
virtual LPTSTR ReadString(
    LPTSTR pstr,  
    UINT nMax);
```  
  
### <a name="parameters"></a>Parametry  
 `pstr`  
 Wskaźnik do ciągu, który zostanie wyświetlony wiersz odczytu.  
  
 `nMax`  
 Maksymalna liczba znaków do odczytania.  
  
 `rString`  
 Odwołanie do [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) obiekt, który odbiera odczytu wiersza.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do buforu zawierający zwykły dane pobrane z [CInternetFile](../../mfc/reference/cinternetfile-class.md) obiektu. Bez względu na typ danych buforu przekazany do tej metody nie wykonuje wszystkie operacje na danych (na przykład konwersji na format Unicode), więc zwróconych danych musi być zamapowany do struktury spodziewasz się, jak gdyby **void\***  typu zostały zwrócone.  
  
 **Wartość NULL** jeśli osiągnięto koniec pliku przed odczytaniem żadnych danych; lub, jeśli jest to wartość logiczna, **FALSE** czy osiągnięto koniec pliku przed odczytaniem żadnych danych.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja umieszcza wynikowego wiersza w pamięci odwołuje się `pstr` parametru. Zatrzymuje, odczytywanie znaków po dotarciu maksymalną liczbę znaków, określony przez `nMax`. Bufor zawsze odbiera znak końcowy null.  
  
 Jeśli należy wywołać `ReadString` bez wywoływania pierwszego elementu [SetReadBufferSize](#setreadbuffersize), otrzymasz buforu 4096 bajtów.  
  
##  <a name="seek"></a>CInternetFile::Seek  
 Wywołanie tej funkcji Członkowskich, aby przesunąć kursor w uprzednio otwarty plik.  
  
```  
virtual ULONGLONG Seek(
    LONGLONG lOffset,  
    UINT nFrom);
```  
  
### <a name="parameters"></a>Parametry  
 `lOffset`  
 Przesunięcie w bajtach, aby przenieść wskaźnik odczytu/zapisu w pliku.  
  
 `nFrom`  
 Odwołanie względne przesunięcia. Musi być jedną z następujących wartości:  
  
- **CFile::begin** przesunięcia wskaźnika pliku `lOff` bajtów w przód od początku pliku.  
  
- **CFile::current** przesunięcia wskaźnika pliku `lOff` bajtów z bieżącej pozycji w pliku.  
  
- **CFile::end** przesunięcia wskaźnika pliku `lOff` bajtów na końcu pliku. `lOff`może być ujemna do wyszukania z istniejącym plikiem; wartości dodatnie będzie wyszukiwać poza końcem pliku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Przesunięcie od początku pliku, jeśli żądana pozycja jest dozwolony; nowy bajtów w przeciwnym razie wartość jest niezdefiniowana i [CInternetException](../../mfc/reference/cinternetexception-class.md) obiekt jest generowany.  
  
### <a name="remarks"></a>Uwagi  
 `Seek` Funkcji zezwala na dostępie do zawartości pliku Przesuń wskaźnik określonym, absolutnie lub względnie. Nie są faktycznie odczytywane dane podczas wyszukiwania.  
  
 W tej chwili wywołanie funkcji członkowskiej jest obsługiwana tylko dla danych skojarzonych z `CHttpFile` obiektów. Nie jest obsługiwana dla żądań FTP lub gopher. Jeśli należy wywołać `Seek` dla jednej z tych usług nieobsługiwany go będzie przesłać możesz kod błędu Win32 **ERROR_INTERNET_INVALID_OPERATION**.  
  
 Po otwarciu pliku wskaźnika pliku jest przy przesunięciu 0, początku pliku.  
  
> [!NOTE]
>  Przy użyciu `Seek` może spowodować niejawne wywołanie [opróżnić](#flush).  
  
### <a name="example"></a>Przykład  
  Zobacz przykład implementacji klasy podstawowej ( [CFile::Seek](../../mfc/reference/cfile-class.md#seek)).  
  
##  <a name="setreadbuffersize"></a>CInternetFile::SetReadBufferSize  
 Wywołanie tej funkcji Członkowskich ustawia rozmiar buforu odczytu tymczasowy używany przez `CInternetFile`-pochodzi z obiektu.  
  
```  
BOOL SetReadBufferSize(UINT nReadSize);
```  
  
### <a name="parameters"></a>Parametry  
 *nReadSize*  
 Bufor żądany rozmiar w bajtach.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0. W przypadku niepowodzenia wywołania funkcji Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) może zostać wywołana w celu ustalenia przyczyny błędu.  
  
### <a name="remarks"></a>Uwagi  
 Podstawowych interfejsów API usługi WinInet nie wykonać buforowanie, więc wybrać rozmiaru buforu, który pozwala aplikacji na odczytywanie danych, niezależnie od ilości danych do odczytu. W przypadku każdego wywołania w celu [odczytu](#read) zwykle obejmuje aount dużych danych (na przykład w kilobajtach cztery lub więcej), nie należy buforu. Jednak jeśli wywołujesz **odczytu** uzyskanie małych fragmentów danych, lub jeśli używasz [ReadString](#readstring) odczytać poszczególnych wierszy w czasie, buforu odczytu poprawia wydajność aplikacji, a następnie.  
  
 Domyślnie `CInternetFile` obiekt nie ma żadnych buforowania do odczytu. Wywołanie funkcji członkowskiej, należy się upewnić, że plik został otwarty do odczytu.  
  
 Można zwiększyć rozmiar buforu w dowolnym momencie, ale zmniejszanie buforu nie odniesie żadnego skutku. Jeśli należy wywołać [ReadString](#readstring) bez wywoływania pierwszego elementu `SetReadBufferSize`, otrzymasz buforu 4096 bajtów.  
  
##  <a name="setwritebuffersize"></a>CInternetFile::SetWriteBufferSize  
 Wywołanie tej funkcji elementu członkowskiego, aby ustawić rozmiar buforu zapisu tymczasowy używany przez `CInternetFile`-pochodzi z obiektu.  
  
```  
BOOL SetWriteBufferSize(UINT nWriteSize);
```  
  
### <a name="parameters"></a>Parametry  
 *nWriteSize*  
 Rozmiar buforu w bajtach.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0. W przypadku niepowodzenia wywołania funkcji Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) może zostać wywołana w celu ustalenia przyczyny błędu.  
  
### <a name="remarks"></a>Uwagi  
 Dlatego podstawowych interfejsów API usługi WinInet nie dokonuj buforowania, wybierz rozmiaru buforu, który pozwala aplikacji do zapisania danych wydajnie niezależnie od ilości danych do zapisania. W przypadku każdego wywołania w celu [zapisu](#write) zwykle obejmuje dużą ilość danych (na przykład co najmniej czterema kilobajtów jednocześnie), nie należy buforu. Jednak jeśli wywołujesz [zapisu](#write) zapisu małych fragmentów danych, bufor zapisu zwiększa wydajność aplikacji.  
  
 Domyślnie `CInternetFile` obiekt nie ma żadnych buforowanie zapisu. Wywołanie funkcji członkowskiej, należy się upewnić, że plik został otwarty do zapisu. Rozmiar buforu zapisu można zmienić w dowolnym momencie, ale powoduje to wywołanie niejawne [opróżnić](#flush).  
  
##  <a name="write"></a>CInternetFile::Write  
 Wywołanie tej funkcji Członkowskich do zapisu w danym pamięci `lpvBuf`, określona liczba bajtów, `nCount`.  
  
```  
virtual void Write(
    const void* lpBuf,  
    UINT nCount);
```  
  
### <a name="parameters"></a>Parametry  
 `lpBuf`  
 Wskaźnik do pierwszego bajtu do zapisania.  
  
 `nCount`  
 Określa liczbę bajtów do zapisania.  
  
### <a name="remarks"></a>Uwagi  
 W przypadku błędu podczas zapisywania danych, funkcja zwraca [CInternetException](../../mfc/reference/cinternetexception-class.md) obiektu opisem błędu.  
  
##  <a name="writestring"></a>CInternetFile::WriteString  
 Ta funkcja zapisuje skojarzony plik ciąg znaków zakończony znakiem null.  
  
```  
virtual void WriteString(LPCTSTR pstr);
```  
  
### <a name="parameters"></a>Parametry  
 `pstr`  
 Wskaźnik do ciąg zawierający zawartość do zapisania.  
  
### <a name="remarks"></a>Uwagi  
 W przypadku błędu podczas zapisywania danych, funkcja zwraca [CInternetException](../../mfc/reference/cinternetexception-class.md) obiektu opisem błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CStdioFile](../../mfc/reference/cstdiofile-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CInternetConnection](../../mfc/reference/cinternetconnection-class.md)
