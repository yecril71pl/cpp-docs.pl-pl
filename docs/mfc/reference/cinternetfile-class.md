---
title: Klasa CInternetFile
ms.date: 11/04/2016
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
ms.openlocfilehash: e3f1a7167f5464423754951764c4441513197841
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372399"
---
# <a name="cinternetfile-class"></a>Klasa CInternetFile

Umożliwia dostęp do plików w systemach zdalnych korzystających z protokołów internetowych.

## <a name="syntax"></a>Składnia

```
class CInternetFile : public CStdioFile
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[CInternetFile::CInternetFile](#cinternetfile)|Konstruuje `CInternetFile` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Plik CInternet::Przerwanie](#abort)|Zamyka plik, ignorując wszystkie ostrzeżenia i błędy.|
|[CInternetFile::Zamknij](#close)|Zamyka `CInternetFile` i uwalnia swoje zasoby.|
|[CInternetFile::Flush](#flush)|Opróżnia zawartość buforu zapisu i upewnia się, że dane w pamięci są zapisywane na komputerze docelowym.|
|[Plik CInternetFile::GetLength](#getlength)|Zwraca rozmiar pliku.|
|[CInternetFile::Odczyt](#read)|Odczytuje liczbę określonych bajtów.|
|[CInternetFile::ReadString](#readstring)|Odczytuje strumień znaków.|
|[Plik CInternet::Szukaj](#seek)|Zmienia położenie wskaźnika w otwartym pliku.|
|[CInternetFile::SetReadBufferSize](#setreadbuffersize)|Ustawia rozmiar buforu, w którym będą odczytywane dane.|
|[CInternetFile::SetWriteBufferSize](#setwritebuffersize)|Ustawia rozmiar buforu, w którym będą zapisywane dane.|
|[CInternetFile::Napisz](#write)|Zapisuje liczbę określonych bajtów.|
|[CInternetFile::WriteString](#writestring)|Zapisuje ciąg zakończony zerem do pliku.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CInternetFile::operator HINTERNET](#operator_hinternet)|Operator odlewania dla uchwytu internetowego.|

### <a name="protected-data-members"></a>Członkowie chronionych danych

|Nazwa|Opis|
|----------|-----------------|
|[CInternetFile::m_hFile](#m_hfile)|Dojście do pliku.|

## <a name="remarks"></a>Uwagi

Udostępnia klasę podstawową dla klas plików [CHttpFile](../../mfc/reference/chttpfile-class.md) i [CGopherFile.](../../mfc/reference/cgopherfile-class.md) Nigdy nie `CInternetFile` tworzysz obiektu bezpośrednio. Zamiast tego utwórz obiekt jednej z klas pochodnych, wywołując [CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) lub [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest). Obiekt można również `CInternetFile` utworzyć, wywołując [CFtpConnection::OpenFile](../../mfc/reference/cftpconnection-class.md#openfile).

Funkcje `CInternetFile` `Open`członkowskie `LockRange` `UnlockRange`, `Duplicate` , i nie `CInternetFile`są implementowane dla . Jeśli wywołasz te `CInternetFile` funkcje na obiekcie, otrzymasz [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Aby dowiedzieć `CInternetFile` się więcej o tym, jak działa z innymi klasami MFC Internet, zobacz artykuł [Programowanie internetowe z WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Cfile](../../mfc/reference/cfile-class.md)

[Cstdiofile](../../mfc/reference/cstdiofile-class.md)

`CInternetFile`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxinet.h

## <a name="cinternetfileabort"></a><a name="abort"></a>Plik CInternet::Przerwanie

Zamyka plik skojarzony z tym obiektem i sprawia, że plik jest niedostępny do odczytu lub zapisu.

```
virtual void Abort();
```

### <a name="remarks"></a>Uwagi

Jeśli plik nie został zamknięty przed zniszczeniem obiektu, destruktor zamknie go za Ciebie.

Podczas obsługi wyjątków, `Abort` różni się od [Close](#close) na dwa ważne sposoby. Po pierwsze `Abort` funkcja nie zgłasza wyjątek na błędy, ponieważ ignoruje błędy. Po `Abort` drugie nie **assert,** jeśli plik nie został otwarty lub został zamknięty wcześniej.

## <a name="cinternetfilecinternetfile"></a><a name="cinternetfile"></a>CInternetFile::CInternetFile

Ta funkcja elementu członkowskiego `CInternetFile` jest wywoływana podczas tworzenia obiektu.

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

*hFile (plik)*<br/>
Dojście do pliku internetowego.

*nazwa pliku pstrFile*<br/>
Wskaźnik do ciągu zawierającego nazwę pliku.

*pZkładanie*<br/>
Wskaźnik do [obiektu CInternetConnection.](../../mfc/reference/cinternetconnection-class.md)

*bCzyciek*<br/>
Wskazuje, czy plik jest tylko do odczytu.

*hSession (wysiew)*<br/>
Dojście do sesji internetowej.

*pstrServer (serwer pstrServer)*<br/>
Wskaźnik do ciągu zawierającego nazwę serwera.

*Dwcontext*<br/>
Identyfikator kontekstu `CInternetFile` obiektu. Zobacz [Podstawy wininet, aby](../../mfc/wininet-basics.md) uzyskać więcej informacji na temat identyfikatora kontekstu.

### <a name="remarks"></a>Uwagi

Nigdy nie `CInternetFile` tworzysz obiektu bezpośrednio. Zamiast tego utwórz obiekt jednej z klas pochodnych, wywołując [CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) lub [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest). Obiekt można również `CInternetFile` utworzyć, wywołując [CFtpConnection::OpenFile](../../mfc/reference/cftpconnection-class.md#openfile).

## <a name="cinternetfileclose"></a><a name="close"></a>CInternetFile::Zamknij

Zamyka `CInternetFile` i uwalnia wszelkie jego zasoby.

```
virtual void Close();
```

### <a name="remarks"></a>Uwagi

Jeśli plik został otwarty do zapisu, istnieje niejawne [wywołanie Flush,](#flush) aby upewnić się, że wszystkie buforowane dane są zapisywane na hoście. Należy wywołać `Close` po zakończeniu korzystania z pliku.

## <a name="cinternetfileflush"></a><a name="flush"></a>CInternetFile::Flush

Wywołanie tej funkcji elementu członkowskiego, aby opróżnić zawartość buforu zapisu.

```
virtual void Flush();
```

### <a name="remarks"></a>Uwagi

Służy `Flush` do zapewnienia, że wszystkie dane w pamięci rzeczywiście zostały zapisane na komputerze docelowym i zapewnić, że transakcja z komputerem hosta została zakończona. `Flush`jest skuteczny `CInternetFile` tylko na obiektach otwartych do pisania.

## <a name="cinternetfilegetlength"></a><a name="getlength"></a>Plik CInternetFile::GetLength

Zwraca rozmiar pliku.

```
virtual ULONGLONG GetLength() const;
```

## <a name="cinternetfilem_hfile"></a><a name="m_hfile"></a>CInternetFile::m_hFile

Dojście do pliku skojarzonego z tym obiektem.

```
HINTERNET m_hFile;
```

## <a name="cinternetfileoperator-hinternet"></a><a name="operator_hinternet"></a>CInternetFile::operator HINTERNET

Ten operator służy do obsługi systemu Windows dla bieżącej sesji internetowej.

```
operator HINTERNET() const;
```

## <a name="cinternetfileread"></a><a name="read"></a>CInternetFile::Odczyt

Wywołanie tej funkcji elementu członkowskiego, aby odczytać do danej pamięci, począwszy od *lpvBuf*, określona liczba bajtów, *nCount*.

```
virtual UINT Read(
    void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Parametry

*lpBuf (właśc.*<br/>
Wskaźnik do adresu pamięci, do którego odczytywane są dane pliku.

*Ncount*<br/>
Liczba bajtów do zapisania.

### <a name="return-value"></a>Wartość zwracana

Liczba bajtów przeniesionych do buforu. Wartość zwracana może być mniejsza niż *nCount,* jeśli osiągnięto koniec pliku.

### <a name="remarks"></a>Uwagi

Funkcja zwraca liczbę bajtów faktycznie odczytanych — liczbę, która może być mniejsza niż *nCount,* jeśli plik się kończy. Jeśli podczas odczytywania pliku wystąpi błąd, funkcja zgłasza [CInternetException](../../mfc/reference/cinternetexception-class.md) obiektu, który opisuje błąd. Należy zauważyć, że odczytywanie po zakończeniu pliku nie jest uważane za błąd i nie zostanie zgłoszony wyjątek.

Aby upewnić się, że wszystkie dane są `CInternetFile::Read` pobierane, aplikacja musi kontynuować wywoływanie metody, dopóki metoda zwraca zero.

## <a name="cinternetfilereadstring"></a><a name="readstring"></a>CInternetFile::ReadString

Wywołanie tej funkcji elementu członkowskiego, aby odczytać strumień znaków, dopóki nie znajdzie znaku nowego.

```
virtual BOOL ReadString(CString& rString);

virtual LPTSTR ReadString(
    LPTSTR pstr,
    UINT nMax);
```

### <a name="parameters"></a>Parametry

*pstr (włas inie*<br/>
Wskaźnik do ciągu, który otrzyma wiersz jest odczytywany.

*Nmax*<br/>
Maksymalna liczba znaków do odczytania.

*rString*<br/>
Odwołanie do [CString](../../atl-mfc-shared/reference/cstringt-class.md) obiektu, który odbiera wiersz odczytu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do buforu zawierający zwykłych danych pobranych z [CInternetFile](../../mfc/reference/cinternetfile-class.md) obiektu. Niezależnie od typu danych buforu przekazywane do tej metody, nie wykonuje żadnych manipulacji na danych (na przykład konwersji do Unicode), więc należy mapować zwrócone dane do struktury, której oczekujesz, tak jakby typ **void** <strong>\*</strong> zostały zwrócone.

NULL, jeśli osiągnięto koniec pliku bez odczytu żadnych danych; lub, jeśli logiczne, FALSE, jeśli koniec pliku został osiągnięty bez odczytu żadnych danych.

### <a name="remarks"></a>Uwagi

Funkcja umieszcza wynikową linię w pamięci, do których odwołuje się parametr *pstr.* Zatrzymuje czytanie znaków, gdy osiągnie maksymalną liczbę znaków, określoną przez *nMax*. Bufor zawsze otrzymuje kończący się znak zerowy.

Jeśli wywołasz `ReadString` bez pierwszego wywołania [SetReadBufferSize](#setreadbuffersize), otrzymasz bufor 4096 bajtów.

## <a name="cinternetfileseek"></a><a name="seek"></a>Plik CInternet::Szukaj

Wywołanie tej funkcji elementu członkowskiego, aby zmienić położenie wskaźnika w wcześniej otwartym pliku.

```
virtual ULONGLONG Seek(
    LONGLONG lOffset,
    UINT nFrom);
```

### <a name="parameters"></a>Parametry

*lStawa*<br/>
Przesunięcie w bajtach, aby przenieść wskaźnik odczytu/zapisu w pliku.

*nZ*<br/>
Względne odwołanie do odsunięcia. Musi mieć jedną z następujących wartości:

- `CFile::begin`Przenoszenie wskaźnika pliku *lOff* bajtów do przodu od początku pliku.

- `CFile::current`Przenieś wskaźnik pliku *lOff* bajty z bieżącej pozycji w pliku.

- `CFile::end`Przenieś wskaźnik pliku *lOff* bajtów od końca pliku. *lOff* musi być ujemny, aby szukać w istniejącym pliku; wartości dodatnie będą poszukiwać po zakończeniu pliku.

### <a name="return-value"></a>Wartość zwracana

Nowy bajt odsunięty od początku pliku, jeśli żądane stanowisko jest legalne; w przeciwnym razie wartość jest niezdefiniowana i [CInternetException](../../mfc/reference/cinternetexception-class.md) obiekt jest generowany.

### <a name="remarks"></a>Uwagi

Funkcja `Seek` umożliwia losowy dostęp do zawartości pliku, przesuwając wskaźnik określoną kwotę, absolutnie lub stosunkowo. Żadne dane nie są faktycznie odczytywane podczas poszukiwania.

W tej chwili wywołanie tej funkcji elementu członkowskiego jest `CHttpFile` obsługiwane tylko dla danych skojarzonych z obiektami. Nie jest obsługiwany dla żądań FTP lub gopher. Jeśli wywołasz `Seek` jedną z tych nieobsługiconych usług, przekaże Cię z powrotem do kodu błędu Win32 ERROR_INTERNET_INVALID_OPERATION.

Po otwarciu pliku wskaźnik pliku jest odsunięty o 0, czyli na początku pliku.

> [!NOTE]
> Użycie `Seek` może spowodować niejawne wywołanie [Flush](#flush).

### <a name="example"></a>Przykład

  Zobacz przykład implementacji klasy podstawowej ( [CFile::Seek](../../mfc/reference/cfile-class.md#seek)).

## <a name="cinternetfilesetreadbuffersize"></a><a name="setreadbuffersize"></a>CInternetFile::SetReadBufferSize

Wywołanie tej funkcji elementu członkowskiego, aby ustawić `CInternetFile`rozmiar tymczasowego buforu odczytu używanego przez obiekt pochodny.

```
BOOL SetReadBufferSize(UINT nReadSize);
```

### <a name="parameters"></a>Parametry

*nCzyszczenie*<br/>
Żądany rozmiar buforu w bajtach.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0. Jeśli wywołanie nie powiedzie się, funkcja Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) może zostać wywołana w celu ustalenia przyczyny błędu.

### <a name="remarks"></a>Uwagi

Podstawowe interfejsy API wininet nie wykonują buforowania, więc wybierz rozmiar buforu, który umożliwia aplikacji do odczytu danych wydajnie, niezależnie od ilości danych do odczytu. Jeśli każde wywołanie [odczytu](#read) zwykle obejmuje dużą aount danych (na przykład cztery lub więcej kilobajtów), nie należy potrzebować buforu. Jednak jeśli wywołasz, `Read` aby uzyskać małe fragmenty danych lub jeśli używasz [ReadString](#readstring) do odczytu poszczególnych wierszy w czasie, a następnie odczytu buforu zwiększa wydajność aplikacji.

Domyślnie `CInternetFile` obiekt nie zapewnia żadnych buforowania do odczytu. Jeśli wywołasz tę funkcję członkową, musisz mieć pewność, że plik został otwarty dla dostępu do odczytu.

Rozmiar buforu można zwiększyć w dowolnym momencie, ale zmniejszanie buforu nie będzie miało wpływu. Jeśli wywołasz [ReadString](#readstring) `SetReadBufferSize`bez pierwszego wywołania, otrzymasz bufor 4096 bajtów.

## <a name="cinternetfilesetwritebuffersize"></a><a name="setwritebuffersize"></a>CInternetFile::SetWriteBufferSize

Wywołanie tej funkcji elementu członkowskiego, aby ustawić `CInternetFile`rozmiar tymczasowego buforu zapisu używanego przez obiekt pochodny.

```
BOOL SetWriteBufferSize(UINT nWriteSize);
```

### <a name="parameters"></a>Parametry

*rozmiar nWiteSize*<br/>
Rozmiar buforu w bajtach.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0. Jeśli wywołanie nie powiedzie się, funkcja Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) może zostać wywołana w celu ustalenia przyczyny błędu.

### <a name="remarks"></a>Uwagi

Podstawowe interfejsy API wininet nie wykonują buforowania, więc wybierz rozmiar buforu, który umożliwia aplikacji do pisania danych wydajnie niezależnie od ilości danych, które mają być zapisywane. Jeśli każde wywołanie [write](#write) zwykle obejmuje dużą ilość danych (na przykład cztery lub więcej kilobajtów naraz), nie należy potrzebować buforu. Jednak jeśli wywołasz [Write](#write) do zapisu małych fragmentów danych, bufor zapisu poprawia wydajność aplikacji.

Domyślnie `CInternetFile` obiekt nie zapewnia buforowania do zapisu. Jeśli wywołasz tę funkcję elementu członkowskiego, musisz mieć pewność, że plik został otwarty dla dostępu do zapisu. Rozmiar buforu zapisu można zmienić w dowolnym momencie, ale powoduje to niejawne wywołanie [Flush](#flush).

## <a name="cinternetfilewrite"></a><a name="write"></a>CInternetFile::Napisz

Wywołanie tej funkcji elementu członkowskiego, aby zapisać w danej pamięci, *lpvBuf*, określona liczba bajtów, *nCount*.

```
virtual void Write(
    const void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Parametry

*lpBuf (właśc.*<br/>
Wskaźnik do pierwszego bajtu, który ma zostać zapisany.

*Ncount*<br/>
Określa liczbę bajtów do zapisania.

### <a name="remarks"></a>Uwagi

Jeśli wystąpi błąd podczas zapisywania danych, funkcja zgłasza [CInternetException](../../mfc/reference/cinternetexception-class.md) obiektu opisującego błąd.

## <a name="cinternetfilewritestring"></a><a name="writestring"></a>CInternetFile::WriteString

Ta funkcja zapisuje ciąg zakończony zerem do skojarzonego pliku.

```
virtual void WriteString(LPCTSTR pstr);
```

### <a name="parameters"></a>Parametry

*pstr (włas inie*<br/>
Wskaźnik do ciągu zawierającego zawartość, która ma zostać zapisana.

### <a name="remarks"></a>Uwagi

Jeśli wystąpi błąd podczas zapisywania danych, funkcja zgłasza [CInternetException](../../mfc/reference/cinternetexception-class.md) obiektu opisującego błąd.

## <a name="see-also"></a>Zobacz też

[Klasa CStdioFile](../../mfc/reference/cstdiofile-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CInternetConnection](../../mfc/reference/cinternetconnection-class.md)
