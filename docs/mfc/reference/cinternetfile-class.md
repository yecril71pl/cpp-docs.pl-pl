---
title: Klasa CInternetFile | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e16aa9377676e415f416dc4f7dae9cb9f2a40dab
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2018
ms.locfileid: "37336569"
---
# <a name="cinternetfile-class"></a>Klasa CInternetFile
Umożliwia dostęp do plików w systemach zdalnych, które korzystają z protokołów internetowych.  
  
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
|[CInternetFile::Abort](#abort)|Zamykanie pliku, ignorując wszystkie ostrzeżenia i błędy.|  
|[CInternetFile::Close](#close)|Zamyka `CInternetFile` i zwalnia jego zasobów.|  
|[CInternetFile::Flush](#flush)|Czyści zawartość buforu zapisu i upewnia się, że dane w pamięci są zapisywane na komputerze docelowym.|  
|[CInternetFile::GetLength](#getlength)|Zwraca rozmiar pliku.|  
|[CInternetFile::Read](#read)|Odczytuje liczby bajtów określonej.|  
|[CInternetFile::ReadString](#readstring)|Odczytuje strumień znaków.|  
|[CInternetFile::Seek](#seek)|Powoduje przeniesienie wskaźnika w otwartego pliku.|  
|[CInternetFile::SetReadBufferSize](#setreadbuffersize)|Ustawia rozmiar buforu, w której będą odczytywane dane.|  
|[CInternetFile::SetWriteBufferSize](#setwritebuffersize)|Ustawia rozmiar buforu, w którym będą zapisywane dane.|  
|[CInternetFile::Write](#write)|Zapisuje liczbę bajtów określoną.|  
|[CInternetFile::WriteString](#writestring)|Zapisuje ciąg zakończony wartością null do pliku.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CInternetFile::operator HINTERNET](#operator_hinternet)|Operator rzutowania dojścia internetowego.|  
  
### <a name="protected-data-members"></a>Chronione elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CInternetFile::m_hFile](#m_hfile)|Dojście do pliku.|  
  
## <a name="remarks"></a>Uwagi  
 Udostępnia klasę bazową dla [CHttpFile](../../mfc/reference/chttpfile-class.md) i [CGopherFile](../../mfc/reference/cgopherfile-class.md) pliku klasy. Nigdy nie twórz `CInternetFile` obiektu bezpośrednio. Zamiast tego utworzyć obiekt w jednej z jej klas pochodnych przez wywołanie metody [CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) lub [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest). Możesz również utworzyć `CInternetFile` obiektu przez wywołanie metody [CFtpConnection::OpenFile](../../mfc/reference/cftpconnection-class.md#openfile).  
  
 `CInternetFile` Elementów członkowskich `Open`, `LockRange`, `UnlockRange`, i `Duplicate` nie są zaimplementowane dla `CInternetFile`. Jeśli chcesz wywołać te funkcje w `CInternetFile` obiektów, zostanie wyświetlony [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).  
  
 Aby dowiedzieć się więcej o tym, jak `CInternetFile` współpracuje z innych klas MFC Internet, zapoznaj się z artykułem [Internet programowanie za pomocą interfejsu WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [CStdioFile](../../mfc/reference/cstdiofile-class.md)  
  
 `CInternetFile`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxinet.h  
  
##  <a name="abort"></a>  CInternetFile::Abort  
 Zamyka plik skojarzony z tym obiektem i sprawia, że plik jest dostępny do odczytu lub zapisu.  
  
```  
virtual void Abort();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli plik nie został zamknięty przed zniszczenia obiektu, destruktor zamyka go dla Ciebie.  
  
 Podczas obsługi wyjątków, `Abort` różni się od [Zamknij](#close) na dwa istotne sposoby. Po pierwsze, `Abort` funkcja nie zgłasza wyjątku na błędy ponieważ ignoruje błędy. Drugi `Abort` nie **ASERCJA** Jeśli plik nie został otwarty lub została wcześniej zamknięta.  
  
##  <a name="cinternetfile"></a>  CInternetFile::CInternetFile  
 Ta funkcja członkowska jest wywoływana, gdy `CInternetFile` obiekt zostanie utworzony.  
  
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
 *hFile —*  
 Dojście do pliku Internet.  
  
 *pstrFileName*  
 Wskaźnik do ciągu zawierającego nazwę pliku.  
  
 *pConnection*  
 Wskaźnik do [CInternetConnection](../../mfc/reference/cinternetconnection-class.md) obiektu.  
  
 *bReadMode*  
 Wskazuje, czy plik jest tylko do odczytu.  
  
 *hSession*  
 Dojście do sesji Internetu.  
  
 *pstrServer*  
 Wskaźnik do ciągu zawierającego nazwę serwera.  
  
 *dwContext*  
 Identyfikator kontekstu `CInternetFile` obiektu. Zobacz [podstawy WinInet](../../mfc/wininet-basics.md) uzyskać więcej informacji o identyfikatorze kontekstu.  
  
### <a name="remarks"></a>Uwagi  
 Nigdy nie twórz `CInternetFile` obiektu bezpośrednio. Zamiast tego utworzyć obiekt w jednej z jej klas pochodnych przez wywołanie metody [CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) lub [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest). Możesz również utworzyć `CInternetFile` obiektu przez wywołanie metody [CFtpConnection::OpenFile](../../mfc/reference/cftpconnection-class.md#openfile).  
  
##  <a name="close"></a>  CInternetFile::Close  
 Zamyka `CInternetFile` i zwalnia jego zasobach.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Uwagi  
 Plik został otwarty do zapisu, czy wywołanie niejawne [opróżniania](#flush) aby mieć pewność, że wszystkie buforowane dane są zapisywane do hosta. Należy wywołać `Close` po zakończeniu, przy użyciu pliku.  
  
##  <a name="flush"></a>  CInternetFile::Flush  
 Wywołaj tę funkcję elementu członkowskiego, aby opróżnić zawartość buforu zapisu.  
  
```  
virtual void Flush();
```  
  
### <a name="remarks"></a>Uwagi  
 Użyj `Flush` aby mieć pewność, że wszystkie dane w pamięci faktycznie został zapisany na komputerze docelowym i upewnić się, ukończono transakcji z komputera hosta. `Flush` obowiązuje tylko na `CInternetFile` obiektów otwarty do zapisu.  
  
##  <a name="getlength"></a>  CInternetFile::GetLength  
 Zwraca rozmiar pliku.  
  
```  
virtual ULONGLONG GetLength() const;  
```  
  
##  <a name="m_hfile"></a>  CInternetFile::m_hFile  
 Dojście do pliku skojarzone z tym obiektem.  
  
```  
HINTERNET m_hFile;  
```  
  
##  <a name="operator_hinternet"></a>  CInternetFile::operator HINTERNET  
 Można pobrać uchwytu Windows dla bieżącej sesji Internet, należy użyć tego operatora.  
  
```  
operator HINTERNET() const;  
```  
  
##  <a name="read"></a>  CInternetFile::Read  
 Wywołaj tę funkcję elementu członkowskiego do odczytu do danego pamięci, zaczynając od *lpvBuf*, określona liczba bajtów, *nCount*.  
  
```  
virtual UINT Read(
    void* lpBuf,  
    UINT nCount);
```  
  
### <a name="parameters"></a>Parametry  
 *lpBuf*  
 Wskaźnik do adresu pamięci, aby plik, który jest do odczytu danych.  
  
 *nCount*  
 Liczba bajtów do zapisania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba bajtów przesłanych w buforze. Zwracana wartość może być mniejsza niż *nCount* jeśli osiągnięto koniec pliku.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja zwraca liczbę bajtów odczytanych w rzeczywistości — liczba, która może być mniejsza niż *nCount* , gdy kończy się w pliku. Jeśli wystąpi błąd podczas odczytywania pliku, funkcja zgłasza [CInternetException](../../mfc/reference/cinternetexception-class.md) obiektu, który opisuje błąd. Należy pamiętać, że odczytu poza końcem pliku nie jest uważany za błąd i zostanie zgłoszony żaden wyjątek.  
  
 Aby upewnić się, wszystkie dane są pobierane, aplikacja musi nadal będą wywoływać `CInternetFile::Read` metody do momentu, metoda zwraca wartość zero.  
  
##  <a name="readstring"></a>  CInternetFile::ReadString  
 Wywołaj tę funkcję elementu członkowskiego, można odczytać strumienia znaków, aż do znalezienia znak nowego wiersza.  
  
```  
virtual BOOL ReadString(CString& rString);

 
virtual LPTSTR ReadString(
    LPTSTR pstr,  
    UINT nMax);
```  
  
### <a name="parameters"></a>Parametry  
 *pstr*  
 Wskaźnik do ciągu, który otrzyma wiersza odczytu.  
  
 *nmaks.*  
 Maksymalna liczba znaków do odczytania.  
  
 *rString*  
 Odwołanie do [CString](../../atl-mfc-shared/reference/cstringt-class.md) obiekt, który odbiera odczytu wiersza.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do buforu zawierający zwykłe dane pobierane z [CInternetFile](../../mfc/reference/cinternetfile-class.md) obiektu. Bez względu na rozmiar buforu przekazanego do tej metody, na typ danych, nie wykonuje wszystkie operacje na danych (na przykład konwersja na Unicode), dzięki czemu zwróconych danych muszą być zmapowana do struktury spodziewasz się, jak gdyby **void\***  typu zostały zwrócone.  
  
 Wartość NULL, jeśli osiągnięto koniec pliku przed odczytaniem żadnych danych; lub, jeśli osiągnięto wartość logiczna, wartość FALSE, jeśli koniec pliku przed odczytaniem danych.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja umieszcza wynikowego wiersza w pamięci, odwołuje się *pstr* parametru. Zatrzymuje, odczytywanie znaków kiedy osiągnie maksymalną liczbę znaków, określony przez *nmaks*. Bufor zawsze będzie otrzymywał kończącego znaku null.  
  
 Jeśli wywołasz `ReadString` bez wywoływania pierwszy [SetReadBufferSize](#setreadbuffersize), otrzymasz bufor 4096 bajtów.  
  
##  <a name="seek"></a>  CInternetFile::Seek  
 Wywołaj tę funkcję elementu członkowskiego, aby przesunąć kursor w wcześniej otwarty plik.  
  
```  
virtual ULONGLONG Seek(
    LONGLONG lOffset,  
    UINT nFrom);
```  
  
### <a name="parameters"></a>Parametry  
 *lOffset*  
 Przesunięcie w bajtach, aby przenieść wskaźnik odczytu/zapisu w pliku.  
  
 *nZe*  
 Odwołania względnego przesunięcia. Musi być jedną z następujących wartości:  
  
- `CFile::begin` Przesuń wskaźnik pliku *lOff* bajtów w przód od początku pliku.  
  
- `CFile::current` Przesuń wskaźnik pliku *lOff* bajtów z bieżącego położenia w pliku.  
  
- `CFile::end` Przesuń wskaźnik pliku *lOff* bajty od końca pliku. *lOff* musi być ujemna do wyszukania w istniejących plików; dodatnie wartości spowoduje przejście poza końcem pliku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Nowe bajtów, przesunięcie od początku pliku, jeśli żądana pozycja jest prawny. w przeciwnym razie wartość jest niezdefiniowana i [CInternetException](../../mfc/reference/cinternetexception-class.md) obiekt jest generowany.  
  
### <a name="remarks"></a>Uwagi  
 `Seek` Funkcji zezwala na losowe dostęp do zawartości pliku, przenosząc kursor określony czas, absolutnie lub stosunkowo. Nie są faktycznie odczytywane dane podczas wyszukiwania.  
  
 W tej chwili wywołanie tej funkcji elementu członkowskiego jest obsługiwana tylko w przypadku danych skojarzonych z `CHttpFile` obiektów. Nie jest obsługiwana dla żądań FTP lub gopher. Jeśli wywołasz `Seek` dla jednego z tych usług nieobsługiwany zostaną przetworzone ponownie możesz ERROR_INTERNET_INVALID_OPERATION kod błędu Win32.  
  
 Po otwarciu pliku wskaźnik pliku znajduje się w przesunięciu 0, na początku pliku.  
  
> [!NOTE]
>  Za pomocą `Seek` może spowodować, że wywołanie niejawne [opróżniania](#flush).  
  
### <a name="example"></a>Przykład  
  Zobacz przykład dla implementacji klasy podstawowej ( [CFile::Seek](../../mfc/reference/cfile-class.md#seek)).  
  
##  <a name="setreadbuffersize"></a>  CInternetFile::SetReadBufferSize  
 Wywołaj tę funkcję elementu członkowskiego, aby ustawić rozmiar tymczasowego buforu odczytu posługują się `CInternetFile`-pochodzi z obiektu.  
  
```  
BOOL SetReadBufferSize(UINT nReadSize);
```  
  
### <a name="parameters"></a>Parametry  
 *nReadSize*  
 Bufor żądany rozmiar w bajtach.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0. W przypadku niepowodzenia wywołania funkcji Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) może zostać wywołana w celu ustalenia przyczyny błędu.  
  
### <a name="remarks"></a>Uwagi  
 Podstawowe interfejsy API WinInet nie wykonać buforowania, więc wybierz rozmiar buforu, który pozwala aplikacji na odczytywanie danych z efektywnością, niezależnie od ilości danych do odczytu. Jeśli wywołanie każdego [odczytu](#read) zwykle obejmuje aount dużych danych (na przykład, w kilobajtach cztery lub więcej), nie należy buforu. Jednak jeśli wywołasz `Read` uzyskanie małych fragmentów danych, lub jeśli używasz [ReadString](#readstring) do odczytania poszczególnych wierszy w czasie, a następnie buforu odczytu zwiększa wydajność aplikacji.  
  
 Domyślnie `CInternetFile` obiektu nie zapewnia żadnych buforowania do odczytu. Jeśli chcesz wywołać tę funkcję elementu członkowskiego, należy się upewnić, że plik został otwarty dostęp do odczytu.  
  
 W dowolnym momencie można zwiększyć rozmiar buforu, ale zmniejszanie buforu odniesie żadnego skutku. Jeśli wywołasz [ReadString](#readstring) bez wywoływania pierwszy `SetReadBufferSize`, otrzymasz bufor 4096 bajtów.  
  
##  <a name="setwritebuffersize"></a>  CInternetFile::SetWriteBufferSize  
 Wywołaj tę funkcję elementu członkowskiego, aby ustawić rozmiar buforu zapisu tymczasowy używany przez `CInternetFile`-pochodzi z obiektu.  
  
```  
BOOL SetWriteBufferSize(UINT nWriteSize);
```  
  
### <a name="parameters"></a>Parametry  
 *nWriteSize*  
 Rozmiar buforu w bajtach.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0. W przypadku niepowodzenia wywołania funkcji Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) może zostać wywołana w celu ustalenia przyczyny błędu.  
  
### <a name="remarks"></a>Uwagi  
 Podstawowe interfejsy API WinInet nie wykonują buforowania, więc wybierz rozmiar buforu, który pozwala aplikacji na zapisywanie danych efektywnie niezależnie od ilości danych ma zostać zapisany. Jeśli wywołanie każdego [zapisu](#write) zwykle obejmuje dużą ilość danych (na przykład co najmniej cztery w kilobajtach na raz), nie należy buforu. Jednak jeśli wywołasz [zapisu](#write) do zapisu małych fragmentów danych, bufor zapisu zwiększa wydajność aplikacji.  
  
 Domyślnie `CInternetFile` obiektu nie zapewnia żadnych buforowanie zapisu. Jeśli chcesz wywołać tę funkcję elementu członkowskiego, należy się upewnić, że plik został otwarty do zapisu. Rozmiar buforu zapisu można zmienić w dowolnym momencie, ale powoduje wywołanie niejawne [opróżniania](#flush).  
  
##  <a name="write"></a>  CInternetFile::Write  
 Wywołanie tej funkcji elementu członkowskiego do zapisu w pamięci danego *lpvBuf*, określona liczba bajtów, *nCount*.  
  
```  
virtual void Write(
    const void* lpBuf,  
    UINT nCount);
```  
  
### <a name="parameters"></a>Parametry  
 *lpBuf*  
 Wskaźnik do pierwszego bajtu do zapisania.  
  
 *nCount*  
 Określa liczbę bajtów do zapisania.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wystąpi jakiś błąd podczas zapisywania danych, funkcja zgłasza [CInternetException](../../mfc/reference/cinternetexception-class.md) Obiekt opisujący błąd.  
  
##  <a name="writestring"></a>  CInternetFile::WriteString  
 Ta funkcja zapisuje ciąg zakończony znakiem null skojarzony plik.  
  
```  
virtual void WriteString(LPCTSTR pstr);
```  
  
### <a name="parameters"></a>Parametry  
 *pstr*  
 Wskaźnik do ciągu zawierającego zawartość do zapisania.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wystąpi jakiś błąd podczas zapisywania danych, funkcja zgłasza [CInternetException](../../mfc/reference/cinternetexception-class.md) Obiekt opisujący błąd.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CStdioFile](../../mfc/reference/cstdiofile-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CInternetConnection](../../mfc/reference/cinternetconnection-class.md)
