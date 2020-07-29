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
ms.openlocfilehash: 460130d98fc9bce761ee293e1a46c86c770b24c9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223073"
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
|[CInternetFile::CInternetFile](#cinternetfile)|Konstruuje `CInternetFile` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CInternetFile:: Abort](#abort)|Zamyka plik, ignorując wszystkie ostrzeżenia i błędy.|
|[CInternetFile:: Close](#close)|Zamyka `CInternetFile` i zwalnia zasoby.|
|[CInternetFile:: Flush](#flush)|Opróżnia zawartość buforu zapisu i gwarantuje, że dane w pamięci są zapisywane na komputerze docelowym.|
|[CInternetFile:: GetLength](#getlength)|Zwraca rozmiar pliku.|
|[CInternetFile:: Read](#read)|Odczytuje liczbę określonych bajtów.|
|[CInternetFile::ReadString](#readstring)|Odczytuje strumień znaków.|
|[CInternetFile:: Seek](#seek)|Zmienia położenie wskaźnika w otwartym pliku.|
|[CInternetFile::SetReadBufferSize](#setreadbuffersize)|Ustawia rozmiar buforu, w którym będą odczytywane dane.|
|[CInternetFile::SetWriteBufferSize](#setwritebuffersize)|Ustawia rozmiar buforu, w którym będą zapisywane dane.|
|[CInternetFile:: Write](#write)|Zapisuje liczbę określonych bajtów.|
|[CInternetFile::WriteString](#writestring)|Zapisuje ciąg zakończony znakiem null do pliku.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CInternetFile:: operator HINTERNET](#operator_hinternet)|Operator rzutowania dla dojścia internetowego.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CInternetFile:: m_hFile](#m_hfile)|Dojście do pliku.|

## <a name="remarks"></a>Uwagi

Udostępnia klasę bazową dla klas plików [CHttpFile](../../mfc/reference/chttpfile-class.md) i [CGopherFile](../../mfc/reference/cgopherfile-class.md) . Nie utworzysz `CInternetFile` bezpośrednio obiektu. Zamiast tego należy utworzyć obiekt jednej z klas pochodnych przez wywołanie [CGopherConnection:: OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) lub [CHttpConnection:: OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest). Można również utworzyć `CInternetFile` obiekt przez wywołanie [CFtpConnection:: OpenFile](../../mfc/reference/cftpconnection-class.md#openfile).

`CInternetFile`Funkcje członkowskie `Open` , `LockRange` , `UnlockRange` i `Duplicate` nie są zaimplementowane dla `CInternetFile` . W przypadku wywołania tych funkcji w `CInternetFile` obiekcie zostanie wyświetlony element [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Aby dowiedzieć się więcej o `CInternetFile` tym, jak działa z innymi klasami internetowymi MFC, zobacz artykuł [programowanie internetowe za pomocą usługi WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

`CInternetFile`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxinet. h

## <a name="cinternetfileabort"></a><a name="abort"></a>CInternetFile:: Abort

Zamyka plik skojarzony z tym obiektem i sprawia, że plik jest niedostępny do odczytu lub zapisu.

```
virtual void Abort();
```

### <a name="remarks"></a>Uwagi

Jeśli plik nie został zamknięty przed zniszczeniem obiektu, destruktor zamknie go.

Obsługa wyjątków różni się `Abort` od [zamykania](#close) na dwa ważne sposoby. Najpierw funkcja nie zgłasza `Abort` wyjątku w przypadku awarii, ponieważ ignoruje błędy. Drugi, nie `Abort` **potwierdza** , czy plik nie został otwarty lub został wcześniej zamknięty.

## <a name="cinternetfilecinternetfile"></a><a name="cinternetfile"></a>CInternetFile::CInternetFile

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

*hFile*<br/>
Dojście do pliku internetowego.

*pstrFileName*<br/>
Wskaźnik do ciągu zawierającego nazwę pliku.

*pConnection*<br/>
Wskaźnik do obiektu [CInternetConnection](../../mfc/reference/cinternetconnection-class.md) .

*Chlebmode*<br/>
Wskazuje, czy plik jest tylko do odczytu.

*hSession*<br/>
Dojście do sesji internetowej.

*pstrServer*<br/>
Wskaźnik do ciągu zawierającego nazwę serwera.

*dwContext*<br/>
Identyfikator kontekstu dla `CInternetFile` obiektu. Aby uzyskać więcej informacji na temat identyfikatora kontekstu, zobacz [podstawy usługi WinInet](../../mfc/wininet-basics.md) .

### <a name="remarks"></a>Uwagi

Nie utworzysz `CInternetFile` bezpośrednio obiektu. Zamiast tego należy utworzyć obiekt jednej z klas pochodnych przez wywołanie [CGopherConnection:: OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) lub [CHttpConnection:: OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest). Można również utworzyć `CInternetFile` obiekt przez wywołanie [CFtpConnection:: OpenFile](../../mfc/reference/cftpconnection-class.md#openfile).

## <a name="cinternetfileclose"></a><a name="close"></a>CInternetFile:: Close

Zamyka `CInternetFile` i zwalnia dowolne z zasobów.

```
virtual void Close();
```

### <a name="remarks"></a>Uwagi

Jeśli plik został otwarty do zapisu, istnieje niejawne wywołanie metody [Flush](#flush) , aby upewnić się, że wszystkie buforowane dane są zapisywane na hoście. Należy wywołać, `Close` gdy skończysz korzystać z pliku.

## <a name="cinternetfileflush"></a><a name="flush"></a>CInternetFile:: Flush

Wywołaj tę funkcję elementu członkowskiego, aby opróżnić zawartość buforu zapisu.

```
virtual void Flush();
```

### <a name="remarks"></a>Uwagi

Użyj `Flush` , aby upewnić się, że wszystkie dane w pamięci zostały rzeczywiście zapisaną na komputerze docelowym i zapewnią, że transakcja z maszyną hosta została ukończona. `Flush`działa tylko w `CInternetFile` przypadku obiektów otwartych do zapisu.

## <a name="cinternetfilegetlength"></a><a name="getlength"></a>CInternetFile:: GetLength

Zwraca rozmiar pliku.

```
virtual ULONGLONG GetLength() const;
```

## <a name="cinternetfilem_hfile"></a><a name="m_hfile"></a>CInternetFile:: m_hFile

Dojście do pliku skojarzonego z tym obiektem.

```
HINTERNET m_hFile;
```

## <a name="cinternetfileoperator-hinternet"></a><a name="operator_hinternet"></a>CInternetFile:: operator HINTERNET

Użyj tego operatora, aby uzyskać uchwyt systemu Windows dla bieżącej sesji internetowej.

```
operator HINTERNET() const;
```

## <a name="cinternetfileread"></a><a name="read"></a>CInternetFile:: Read

Wywołaj tę funkcję elementu członkowskiego, aby odczytać w podanej pamięci, rozpoczynając od *lpvBuf*, określoną liczbę bajtów, *nCount*.

```
virtual UINT Read(
    void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Parametry

*lpBuf*<br/>
Wskaźnik do adresu pamięci, do którego odczytywane są dane plików.

*nCount*<br/>
Liczba bajtów do zapisania.

### <a name="return-value"></a>Wartość zwracana

Liczba bajtów przesłanych do buforu. Wartość zwracana może być mniejsza niż *nCount* , jeśli osiągnięto koniec pliku.

### <a name="remarks"></a>Uwagi

Funkcja zwraca liczbę bajtów, które są faktycznie odczytywane — liczba, która może być mniejsza niż *nCount* , jeśli plik zostanie zakończony. Jeśli wystąpi błąd podczas odczytywania pliku, funkcja zgłasza obiekt [CInternetException](../../mfc/reference/cinternetexception-class.md) , który opisuje błąd. Należy zauważyć, że odczyt poza końcem pliku nie jest uważany za błąd i nie zostanie zgłoszony żaden wyjątek.

Aby upewnić się, że wszystkie dane są pobierane, aplikacja musi kontynuować wywoływanie `CInternetFile::Read` metody, dopóki metoda nie zwróci wartości zero.

## <a name="cinternetfilereadstring"></a><a name="readstring"></a>CInternetFile::ReadString

Wywołaj tę funkcję elementu członkowskiego, aby odczytać strumień znaków do momentu znalezienia znaku nowego wiersza.

```
virtual BOOL ReadString(CString& rString);

virtual LPTSTR ReadString(
    LPTSTR pstr,
    UINT nMax);
```

### <a name="parameters"></a>Parametry

*pstr*<br/>
Wskaźnik do ciągu, który otrzyma odczytywany wiersz.

*Nmaks.*<br/>
Maksymalna liczba znaków, które mają zostać odczytane.

*rString*<br/>
Odwołanie do obiektu [CString](../../atl-mfc-shared/reference/cstringt-class.md) , który odbiera odczytany wiersz.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do buforu zawierającego zwykłe dane pobierane z obiektu [CInternetFile](../../mfc/reference/cinternetfile-class.md) . Bez względu na typ danych buforu przekazana do tej metody nie wykonuje żadnych operacji związanych z danymi (na przykład konwersji do formatu Unicode), więc należy zamapować zwrócone dane na oczekiwaną strukturę, tak jakby **`void`** <strong>\*</strong> był zwracany typ.

Wartość NULL, jeśli koniec pliku został osiągnięty bez odczytywania danych; lub, jeśli wartość logiczna jest RÓWNa FALSE, jeśli koniec pliku został osiągnięty bez odczytywania danych.

### <a name="remarks"></a>Uwagi

Funkcja umieszcza dany wiersz w pamięci, do której odwołuje się parametr *PSTR* . Po osiągnięciu maksymalnej liczby znaków, określonej przez *nmaks.*, przestaje odczytywane znaki. Bufor zawsze otrzymuje kończący znak null.

W przypadku wywołania `ReadString` bez uprzedniego wywołania [SetReadBufferSize](#setreadbuffersize)otrzymasz bufor 4096 bajtów.

## <a name="cinternetfileseek"></a><a name="seek"></a>CInternetFile:: Seek

Wywołaj tę funkcję elementu członkowskiego, aby zmienić położenie wskaźnika w wcześniej otwartym pliku.

```
virtual ULONGLONG Seek(
    LONGLONG lOffset,
    UINT nFrom);
```

### <a name="parameters"></a>Parametry

*lOffset*<br/>
Przesunięcie w bajtach, aby przenieść wskaźnik odczytu/zapisu w pliku.

*NZE*<br/>
Odwołanie względne dla przesunięcia. Musi mieć jedną z następujących wartości:

- `CFile::begin`Przenieś wskaźnik pliku *lOff* bajty do przodu od początku pliku.

- `CFile::current`Przenieś wskaźnik pliku *lOff* bajty z bieżącej pozycji w pliku.

- `CFile::end`Przenieś wskaźnik pliku *lOff* bajty z końca pliku. *lOff* musi być ujemna, aby przeszukać istniejący plik; wartości dodatnie będą przebiegać poza końcem pliku.

### <a name="return-value"></a>Wartość zwracana

Wartość przesunięcia nowego bajtu od początku pliku, jeśli żądana pozycja ma charakter prawny; w przeciwnym razie wartość jest niezdefiniowana i zostanie zgłoszony obiekt [CInternetException](../../mfc/reference/cinternetexception-class.md) .

### <a name="remarks"></a>Uwagi

`Seek`Funkcja zezwala na losowy dostęp do zawartości pliku przez przeniesienie wskaźnika o określoną ilość, absolutną lub względną. Podczas wyszukiwania nie są faktycznie odczytywane żadne dane.

W tej chwili wywołanie tej funkcji składowej jest obsługiwane tylko dla danych skojarzonych z `CHttpFile` obiektami. Nie jest obsługiwana w przypadku żądań FTP i gopher. Jeśli wywołasz `Seek` dla jednej z tych nieobsługiwanych usług, nastąpi powrót do kodu błędu Win32 ERROR_INTERNET_INVALID_OPERATION.

Gdy plik zostanie otwarty, wskaźnik pliku jest przesunięty o 0, początek pliku.

> [!NOTE]
> Użycie `Seek` może spowodować niejawne wywołanie do [opróżniania](#flush).

### <a name="example"></a>Przykład

  Zobacz przykład implementacji klasy bazowej ( [CFile:: Seek](../../mfc/reference/cfile-class.md#seek)).

## <a name="cinternetfilesetreadbuffersize"></a><a name="setreadbuffersize"></a>CInternetFile::SetReadBufferSize

Wywołaj tę funkcję elementu członkowskiego, aby ustawić rozmiar tymczasowego buforu odczytu używanego przez `CInternetFile` obiekt pochodny.

```
BOOL SetReadBufferSize(UINT nReadSize);
```

### <a name="parameters"></a>Parametry

*nReadSize*<br/>
Żądany rozmiar buforu w bajtach.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0. Jeśli wywołanie nie powiedzie się, może zostać wywołana [wartość GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) funkcji Win32, aby określić przyczynę błędu.

### <a name="remarks"></a>Uwagi

Bazowe interfejsy API platformy WinInet nie wykonują buforowania, więc wybierz rozmiar buforu, który umożliwia aplikacji wydajne odczytywanie danych, niezależnie od ilości danych, które mają być odczytywane. Jeśli każde wywołanie metody [Read](#read) zwykle obejmuje duże aount danych (na przykład cztery lub więcej kilobajtów), nie należy potrzebować buforu. Jednak w przypadku wywołania `Read` programu w celu pobrania małych fragmentów danych lub w przypadku korzystania z [ReadString](#readstring) w celu odczytania poszczególnych wierszy w danym momencie bufor odczytu poprawi wydajność aplikacji.

Domyślnie `CInternetFile` obiekt nie zapewnia buforowania do odczytu. W przypadku wywołania tej funkcji elementu członkowskiego należy upewnić się, że plik został otwarty na potrzeby dostępu do odczytu.

Rozmiar buforu można zwiększyć w dowolnym momencie, ale zmniejszenie rozmiaru buforu nie będzie miało żadnego efektu. Jeśli wywołasz [ReadString](#readstring) bez uprzedniego wywołania, otrzymasz `SetReadBufferSize` bufor 4096 bajtów.

## <a name="cinternetfilesetwritebuffersize"></a><a name="setwritebuffersize"></a>CInternetFile::SetWriteBufferSize

Wywołaj tę funkcję elementu członkowskiego, aby ustawić rozmiar buforu zapisu tymczasowego używanego przez `CInternetFile` obiekt pochodny.

```
BOOL SetWriteBufferSize(UINT nWriteSize);
```

### <a name="parameters"></a>Parametry

*nWriteSize*<br/>
Rozmiar buforu w bajtach.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0. Jeśli wywołanie nie powiedzie się, może zostać wywołana [wartość GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) funkcji Win32, aby określić przyczynę błędu.

### <a name="remarks"></a>Uwagi

Bazowe interfejsy API usługi WinInet nie wykonują buforowania, więc wybierz rozmiar buforu, który pozwala aplikacji efektywnie zapisywać dane niezależnie od ilości danych, które mają zostać zapisane. Jeśli każde wywołanie do [zapisu](#write) zwykle obejmuje dużą ilość danych (na przykład cztery lub więcej kilobajtów w danym momencie), nie należy potrzebować buforu. Jednak w przypadku wywołania [zapisu](#write) w celu zapisania małych fragmentów danych bufor zapisu poprawi wydajność aplikacji.

Domyślnie `CInternetFile` obiekt nie udostępnia buforowania do zapisu. W przypadku wywołania tej funkcji elementu członkowskiego należy upewnić się, że plik został otwarty do zapisu. Rozmiar buforu zapisu można zmienić w dowolnym momencie, ale spowoduje to niejawne wywołanie do [opróżniania](#flush).

## <a name="cinternetfilewrite"></a><a name="write"></a>CInternetFile:: Write

Wywołaj tę funkcję elementu członkowskiego, aby zapisać w podanej pamięci, *lpvBuf*, określoną liczbę bajtów, *nCount*.

```
virtual void Write(
    const void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Parametry

*lpBuf*<br/>
Wskaźnik do pierwszego bajtu do zapisania.

*nCount*<br/>
Określa liczbę bajtów do zapisania.

### <a name="remarks"></a>Uwagi

Jeśli wystąpi błąd podczas zapisywania danych, funkcja zgłasza obiekt [CInternetException](../../mfc/reference/cinternetexception-class.md) opisujący błąd.

## <a name="cinternetfilewritestring"></a><a name="writestring"></a>CInternetFile::WriteString

Ta funkcja zapisuje ciąg zakończony znakiem null w skojarzonym pliku.

```
virtual void WriteString(LPCTSTR pstr);
```

### <a name="parameters"></a>Parametry

*pstr*<br/>
Wskaźnik do ciągu zawierającego zawartość do zapisania.

### <a name="remarks"></a>Uwagi

Jeśli wystąpi błąd podczas zapisywania danych, funkcja zgłasza obiekt [CInternetException](../../mfc/reference/cinternetexception-class.md) opisujący błąd.

## <a name="see-also"></a>Zobacz także

[Klasa CStdioFile](../../mfc/reference/cstdiofile-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CInternetConnection](../../mfc/reference/cinternetconnection-class.md)
