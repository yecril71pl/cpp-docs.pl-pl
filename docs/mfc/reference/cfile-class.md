---
title: Klasa CFile
ms.date: 06/12/2018
f1_keywords:
- CFile
- AFX/CFile
- AFX/CFile::CFile
- AFX/CFile::Abort
- AFX/CFile::Close
- AFX/CFile::Duplicate
- AFX/CFile::Flush
- AFX/CFile::GetFileName
- AFX/CFile::GetFilePath
- AFX/CFile::GetFileTitle
- AFX/CFile::GetLength
- AFX/CFile::GetPosition
- AFX/CFile::GetStatus
- AFX/CFile::LockRange
- AFX/CFile::Open
- AFX/CFile::Read
- AFX/CFile::Remove
- AFX/CFile::Rename
- AFX/CFile::Seek
- AFX/CFile::SeekToBegin
- AFX/CFile::SeekToEnd
- AFX/CFile::SetFilePath
- AFX/CFile::SetLength
- AFX/CFile::SetStatus
- AFX/CFile::UnlockRange
- AFX/CFile::Write
- AFX/CFile::hFileNull
- AFX/CFile::m_hFile
- AFX/CFile::m_pTM
helpviewer_keywords:
- CFile [MFC], CFile
- CFile [MFC], Abort
- CFile [MFC], Close
- CFile [MFC], Duplicate
- CFile [MFC], Flush
- CFile [MFC], GetFileName
- CFile [MFC], GetFilePath
- CFile [MFC], GetFileTitle
- CFile [MFC], GetLength
- CFile [MFC], GetPosition
- CFile [MFC], GetStatus
- CFile [MFC], LockRange
- CFile [MFC], Open
- CFile [MFC], Read
- CFile [MFC], Remove
- CFile [MFC], Rename
- CFile [MFC], Seek
- CFile [MFC], SeekToBegin
- CFile [MFC], SeekToEnd
- CFile [MFC], SetFilePath
- CFile [MFC], SetLength
- CFile [MFC], SetStatus
- CFile [MFC], UnlockRange
- CFile [MFC], Write
- CFile [MFC], hFileNull
- CFile [MFC], m_hFile
- CFile [MFC], m_pTM
ms.assetid: b2eb5757-d499-4e67-b044-dd7d1abaa0f8
ms.openlocfilehash: dcfe2fb30269f3f3a4c14664d9f57f5b937c8c6d
ms.sourcegitcommit: 6cf0c67acce633b07ff31b56cebd5de3218fd733
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2019
ms.locfileid: "67344434"
---
# <a name="cfile-class"></a>Klasa CFile

Klasa bazowa dla klas plików Microsoft Foundation klasy.

## <a name="syntax"></a>Składnia

```
class CFile : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFile::CFile](#cfile)|Konstruuje `CFile` obiekt z uchwyt pliku lub ścieżki.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFile::Abort](#abort)|Zamykanie pliku, ignorując wszystkie ostrzeżenia i błędy.|
|[CFile::Close](#close)|Zamyka plik, a następnie usuwa obiekt.|
|[CFile::Duplicate](#duplicate)|Tworzy obiekt w zduplikowanych na podstawie tego pliku.|
|[CFile::Flush](#flush)|Czyści wszystkie dane do zapisania.|
|[CFile::GetFileName](#getfilename)|Pobiera nazwę wybranego pliku.|
|[CFile::GetFilePath](#getfilepath)|Pobiera pełną ścieżkę pliku wybranego pliku.|
|[CFile::GetFileTitle](#getfiletitle)|Pobiera tytuł wybranego pliku.|
|[CFile::GetLength](#getlength)|Pobiera długość pliku.|
|[CFile::GetPosition](#getposition)|Pobiera bieżący wskaźnik pliku.|
|[CFile::GetStatus](#getstatus)|Pobiera stan, otwórz plik, lub w wersji statycznej, pobiera stan określonego pliku (funkcja statyczne, wirtualne).|
|[CFile::LockRange](#lockrange)|Blokuje zakresu bajtów w pliku.|
|[CFile::Open](#open)|Bezpiecznie otwiera plik z opcjonalnym testowania błędu.|
|[CFile::Read](#read)|Operacje odczytu (niebuforowane) danych z pliku w bieżącym położeniu plików.|
|[CFile::Remove](#remove)|Usuwa określony plik (funkcję statyczną).|
|[CFile::Rename](#rename)|Zmienia nazwę określonego pliku (funkcję statyczną).|
|[CFile::Seek](#seek)|Ustawia bieżący wskaźnik pliku.|
|[CFile::SeekToBegin](#seektobegin)|Ustawia bieżący wskaźnik pliku na początku pliku.|
|[CFile::SeekToEnd](#seektoend)|Ustawia bieżący wskaźnik pliku na końcu pliku.|
|[CFile::SetFilePath](#setfilepath)|Ustawia pełną ścieżkę pliku wybranego pliku.|
|[CFile::SetLength](#setlength)|Zmienia długość pliku.|
|[CFile::SetStatus](#setstatus)|Ustawia stan określonego pliku (funkcja statyczne, wirtualne).|
|[CFile::UnlockRange](#unlockrange)|Odblokowuje zakresu bajtów w pliku.|
|[CFile::Write](#write)|Operacje zapisu (niebuforowane) danych w pliku do bieżącego położenia pliku.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFile::operator UCHWYTU](#operator_handle)|Dojście do `CFile` obiektu.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CFile::hFileNull](#hfilenull)|Określa, czy `CFile` obiekt ma prawidłowy uchwyt.|
|[CFile::m_hFile](#m_hfile)|Zazwyczaj zawiera dojście do pliku systemu operacyjnego.|

### <a name="protected-data-members"></a>Chronione elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CFile::m_pTM](#m_ptm)|Wskaźnik do `CAtlTransactionManager` obiektu.|

## <a name="remarks"></a>Uwagi

Bezpośrednio zapewnia usługi wejścia/wyjścia dysku Niebuforowane, binarne, przy czym pośrednio obsługuje pliki tekstowe i pliki pamięci za pomocą jej klas pochodnych. `CFile` działa w połączeniu z `CArchive` klasy do obsługi serializacji obiektów MFC.

Hierarchiczna relacja między tej klasy i jej klasy pochodne umożliwia program, aby działać na wszystkich obiektach pliku za pośrednictwem polimorficznych `CFile` interfejsu. Plik pamięci, na przykład, zachowuje się jak pliku na dysku.

Użyj `CFile` i jej klasy pochodne dla ogólnego zastosowania we/wy dysku. Użyj `ofstream` lub innych firmy Microsoft `iostream` klasy dla tekstu sformatowanego wysyłane do pliku na dysku.

Zwykle pliku na dysku jest otwierany automatycznie na `CFile` konstruowaniem i niszczeniem zamknięty na. Statyczne funkcje Członkowskie pozwalają na potrzeby analizowania pliku stanu bez otwierania pliku.

Aby uzyskać więcej informacji na temat korzystania z `CFile`, zobacz artykuły [pliki w MFC](../../mfc/files-in-mfc.md) i [Obsługa plików](../../c-runtime-library/file-handling.md) w *odwołanie do biblioteki wykonawczej*.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CFile`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="abort"></a>  CFile::Abort

Zamyka plik skojarzony z tym obiektem i sprawia, że plik jest dostępny do odczytu lub zapisu.

```
virtual void Abort();
```

### <a name="remarks"></a>Uwagi

Jeśli plik nie został zamknięty przed zniszczenia obiektu, destruktor zamyka go dla Ciebie.

Podczas obsługi wyjątków, `CFile::Abort` różni się od `CFile::Close` na dwa istotne sposoby. Po pierwsze, `Abort` funkcja nie będzie zgłosić wyjątek na awarie, ponieważ błędy są ignorowane przez `Abort`. Drugi `Abort` nie **ASERCJA** Jeśli plik nie został otwarty lub została wcześniej zamknięta.

Jeśli użyto **nowe** przydzielić `CFile` obiektów na stosie, należy je usunąć po zamknięciu pliku. `Abort` Ustawia `m_hFile` do `CFile::hFileNull`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#5](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_1.cpp)]

##  <a name="cfile"></a>  CFile::CFile

Tworzy i inicjuje `CFile` obiektu.

```
CFile();
CFile(CAtlTransactionManager* pTM);
CFile(HANDLE hFile);

CFile(
LPCTSTR lpszFileName,
UINT nOpenFlags);

CFile(
LPCTSTR lpszFileName,
UINT nOpenFlags,
CAtlTransactionManager* pTM);
```

### <a name="parameters"></a>Parametry

*hFile*<br/>
Dojście do pliku, aby dołączyć do `CFile` obiektu.

*lpszFileName*<br/>
Względna lub pełną ścieżkę do pliku do dołączenia do `CFile` obiektu.

*nOpenFlags*<br/>
Bitowa kombinacja (lub) opcje dostępu do plików dla określonego pliku. Zobacz sekcję Spostrzeżenia, aby możliwych opcji.

*pTM*<br/>
Wskaźnik do obiektu CAtlTransactionManager

### <a name="remarks"></a>Uwagi

W poniższych tabelach pięć przedstawiono sposoby, aby *nOpenFlags* parametru.

Wybierz tylko jeden z następujących opcji Tryb dostępu do pliku. Jest to domyślny tryb dostępu do pliku `CFile::modeRead`, który jest tylko do odczytu.

|Wartość|Opis|
|-----------|-----------------|
|`CFile::modeRead`|Żądania dostęp tylko do odczytu.|
|`CFile::modeWrite`|Żądania zapisu wyłącznie.|
|`CFile::modeReadWrite`|Żądania odczytu i zapisu.|

Wybierz jedną z następujących opcji trybu znaków.

|Wartość|Opis|
|-----------|-----------------|
|`CFile::typeBinary`|Ustawia tryb binarny (używane w klasach pochodnych tylko).|
|`CFile::typeText`|Ustawia tryb tekstu przy użyciu specjalnego przetwarzania dla par wysuwu wiersza powrotu karetki (używane w klasach pochodnych tylko).|
|`CFile::typeUnicode`|Ustawia tryb Unicode (używane w klasach pochodnych tylko). Tekst jest pisany w pliku w formacie Unicode, gdy aplikacja jest wliczony w konfiguracji Unicode. Znak BOM nie jest zapisywany do pliku.|

Wybierz tylko jeden z następujących opcji trybu udziału plików. Jest to domyślny tryb udziału pliku `CFile::shareExclusive`, czyli wyłączności.

|Wartość|Opis|
|-----------|-----------------|
|`CFile::shareDenyNone`|Brak ograniczeń do udostępniania.|
|`CFile::shareDenyRead`|Nie zezwala na dostęp do odczytu do wszystkich innych.|
|`CFile::shareDenyWrite`|Nie zezwala na dostęp do zapisu dla wszystkich innych użytkowników.|
|`CFile::shareExclusive`|Nie zezwala na odczyt i zapis dla wszystkich innych użytkowników.|

Wybierz pierwszy lub oba z następujących opcji tryb tworzenia pliku. Jest to domyślny tryb tworzenia `CFile::modeNoTruncate`, czyli otwartych istniejące.

|Wartość|Opis|
|-----------|-----------------|
|`CFile::modeCreate`|Tworzy nowy plik, jeśli plik nie istnieje. Jeśli plik już istnieje, ma zastąpione i początkowo ustawiona zerowej długości.|
|`CFile::modeNoTruncate`|Tworzy nowy plik, jeśli plik nie istnieje; w przeciwnym razie, jeśli plik już istnieje, jest on dołączony do `CFile` obiektu.|

Wybierz plik następujące opcje buforowania, zgodnie z opisem. Domyślnie system używa schemat buforowania ogólnego przeznaczenia, który nie jest dostępna jako opcja.

|Wartość|Opis|
|-----------|-----------------|
|`CFile::osNoBuffer`|System nie używa pośrednich pamięci podręcznej dla pliku. Ta opcja spowoduje anulowanie następujących opcji 2.|
|`CFile::osRandomAccess`|Pamięć podręczna plików jest zoptymalizowany pod kątem dostępu losowego. Nie należy używać zarówno w przypadku tej opcji, jak i opcja sekwencyjne skanowanie.|
|`CFile::osSequentialScan`|Pamięć podręczna plików jest zoptymalizowany pod kątem dostępu sekwencyjnego. Nie należy używać tej opcji i opcji swobodnego dostępu.|
|`CFile::osWriteThrough`|Operacje są wykonywane bez opóźnień zapisu.|

Wybierz następującą opcję zabezpieczeń, aby uniemożliwić są dziedziczone przez dojście do pliku. Domyślnie wszystkie nowe procesy podrzędne służy dojście do pliku.

|Wartość|Opis|
|-----------|-----------------|
|`CFile::modeNoInherit`|Wszystkie procesy podrzędne zapobiega używaniu dojście do pliku.|

Konstruktor domyślny inicjuje elementy członkowskie, ale nie dołączony plik `CFile` obiektu. Po zakończeniu korzystania z tego konstruktora, należy użyć [CFile::Open](#open) metodę, aby otworzyć plik i dołączyć go do `CFile` obiektu.

Konstruktor z jednym parametrem inicjuje elementy członkowskie i dołącza do istniejącego pliku `CFile` obiektu.

Konstruktor z dwoma parametrami inicjuje elementy członkowskie i próbuje otworzyć określonego pliku. Jeśli ten konstruktor pomyślnie otwiera określony plik, plik jest dołączony do `CFile` obiektu; w przeciwnym razie, Konstruktor ten wygeneruje wskaźnik do `CInvalidArgException` obiektu. Aby uzyskać więcej informacji na temat obsługi wyjątków, zobacz [wyjątki](../../mfc/exception-handling-in-mfc.md).

Jeśli `CFile` obiekt zostanie pomyślnie otwarty określony plik, zostanie on zamknięty ten plik automatycznie po `CFile` niszczony jest obiekt; w przeciwnym razie należy jawnie zamknąć go po nie jest już dołączony do `CFile` obiektu.

### <a name="example"></a>Przykład

Poniższy kod przedstawia sposób użycia `CFile`.

[!code-cpp[NVC_MFCFiles#4](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_2.cpp)]

##  <a name="close"></a>  CFile::Close

Zamyka plik skojarzony z tym obiektem i sprawia, że plik jest dostępny do odczytu lub zapisu.

```
virtual void Close();
```

### <a name="remarks"></a>Uwagi

Jeśli plik nie został zamknięty przed zniszczenia obiektu, destruktor zamyka go dla Ciebie.

Jeśli użyto **nowe** przydzielić `CFile` obiektów na stosie, należy je usunąć po zamknięciu pliku. `Close` Ustawia `m_hFile` do `CFile::hFileNull`.

### <a name="example"></a>Przykład

Zobacz przykład [CFile::CFile](#cfile).

##  <a name="duplicate"></a>  CFile::Duplicate

Tworzy duplikat `CFile` obiektu dla danego pliku.

```
virtual CFile* Duplicate() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do duplikat `CFile` obiektu.

### <a name="remarks"></a>Uwagi

Ta funkcja jest odpowiednikiem funkcji wykonawczej C `_dup`.

##  <a name="flush"></a>  CFile::Flush

Wymusza wszelkie dane pozostały w buforze plików, które są zapisywane w pliku.

```
virtual void Flush();
```

### <a name="remarks"></a>Uwagi

Korzystanie z `Flush` nie gwarantuje opróżnianie `CArchive` buforów. Jeśli używasz archiwum wywołać [CArchive::Flush](../../mfc/reference/carchive-class.md#flush) pierwszy.

### <a name="example"></a>Przykład

Zobacz przykład [CFile::SetFilePath](#setfilepath).

##  <a name="getfilename"></a>  CFile::GetFileName

Wywołaj tę funkcję elementu członkowskiego, aby pobrać nazwę określonego pliku.

```
virtual CString GetFileName() const;
```

### <a name="return-value"></a>Wartość zwracana

Nazwa pliku.

### <a name="remarks"></a>Uwagi

Na przykład gdy wywołujesz `GetFileName` do generowania wiadomość do użytkownika o pliku `c:\windows\write\myfile.wri`, nazwę pliku, `myfile.wri`, jest zwracana.

Aby przywrócić pełną ścieżkę pliku, łącznie z nazwą wywołać [GetFilePath](#getfilepath). Aby przywrócić tytuł pliku ( `myfile`), wywołaj [GetFileTitle](#getfiletitle).

### <a name="example"></a>Przykład

Ten fragment kodu otwiera SYSTEM. Pliku INI w katalogu systemu WINDOWS. Jeśli znaleziono przykładzie zostanie wydrukowana nazwę i ścieżkę oraz tytuł, jak pokazano w danych wyjściowych:

[!code-cpp[NVC_MFCFiles#6](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_3.cpp)]

##  <a name="getfilepath"></a>  CFile::GetFilePath

Wywołaj tę funkcję elementu członkowskiego, aby pobrać pełną ścieżkę określonego pliku.

```
virtual CString GetFilePath() const;
```

### <a name="return-value"></a>Wartość zwracana

Pełna ścieżka określonego pliku.

### <a name="remarks"></a>Uwagi

Na przykład gdy wywołujesz `GetFilePath` do generowania wiadomość do użytkownika o pliku `c:\windows\write\myfile.wri`, ścieżkę pliku `c:\windows\write\myfile.wri`, jest zwracana.

Aby zwrócić tylko nazwę pliku (`myfile.wri`), wywołaj [GetFileName](#getfilename). Aby przywrócić tytuł pliku (`myfile`), wywołaj [GetFileTitle](#getfiletitle).

### <a name="example"></a>Przykład

Zobacz przykład [GetFileName](#getfilename).

##  <a name="getfiletitle"></a>  CFile::GetFileTitle

Wywołaj tę funkcję elementu członkowskiego, można pobrać nazwy pliku (nazwa wyświetlana) dla pliku.

```
virtual CString GetFileTitle() const;
```

### <a name="return-value"></a>Wartość zwracana

Tytuł pliku podstawowego.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [GetFileTitle](/windows/desktop/api/commdlg/nf-commdlg-getfiletitlea) można pobrać nazwy pliku. Jeśli to się powiedzie, metoda zwraca ciąg, który będzie używane w systemie aby wyświetlić nazwę pliku do użytkownika. W przeciwnym razie metoda wywołuje [PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea) pobrać nazwy pliku (łącznie z rozszerzeniem pliku) pliku podstawowego. Oznacza to, że rozszerzenie pliku nie jest zawsze zawarty w pliku zwracany ciąg tytułu. Aby uzyskać więcej informacji, zobacz [GetFileTitle](/windows/desktop/api/commdlg/nf-commdlg-getfiletitlea) i [PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea) w zestawie Windows SDK.

Aby przywrócić pełną ścieżkę pliku, łącznie z nazwą wywołać [GetFilePath](#getfilepath). Aby zwracać tylko nazwę pliku, należy wywołać [GetFileName](#getfilename).

### <a name="example"></a>Przykład

Zobacz przykład [GetFileName](#getfilename).

##  <a name="getlength"></a>  CFile::GetLength

Uzyskuje bieżącą logiczne długość pliku w bajtach.

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>Wartość zwracana

Długość pliku.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#7](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_4.cpp)]

##  <a name="getposition"></a>  CFile::GetPosition

Uzyskuje bieżącą wartość wskaźnika pliku, którego można użyć w późniejszym wywołania `Seek`.

```
virtual ULONGLONG GetPosition() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik pliku.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#8](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_5.cpp)]

##  <a name="getstatus"></a>  CFile::GetStatus

Ta metoda umożliwia pobranie informacji o stanie związane z danym `CFile` wystąpienie obiektu lub ścieżką danego pliku.

```
BOOL GetStatus(CFileStatus& rStatus) const;

static BOOL PASCAL GetStatus(
    LPCTSTR lpszFileName,
    CFileStatus& rStatus,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*rStatus*<br/>
Odwołanie do podanego użytkownika `CFileStatus` struktury, który będzie otrzymywać informacje o stanie. `CFileStatus` Struktura zawiera następujące pola:

- `CTime m_ctime` Data i godzina utworzenia pliku.

- `CTime m_mtime` Data i godzina ostatniej modyfikacji pliku.

- `CTime m_atime` Data i czas ostatniego dostępu do pliku do odczytu.

- `ULONGLONG m_size` Rozmiaru logicznego pliku w bajtach, jak za pomocą polecenia DIR.

- `BYTE m_attribute` Bajt atrybut pliku.

- `char m_szFullName[_MAX_PATH]` Bezwzględnej nazwy pliku w zestawie znaków Windows.

*lpszFileName*<br/>
Ciąg znaków Windows Ustaw to znaczy ścieżka żądanego pliku. Ścieżka może być względna lub bezwzględna lub może zawierać nazwa ścieżki sieciowej.

*pTM*<br/>
Wskaźnik do obiektu CAtlTransactionManager

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli pomyślnie uzyskano informacje o stanie dla określonego pliku; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Niestatyczna wersję `GetStatus` pobiera informacje o stanie z otwartego pliku, które są skojarzone z danym `CFile` obiektu.  Wersji statycznej `GetStatus` uzyskuje informacje o stanie pliku ze ścieżki plików danego bez konieczności otwierania pliku. Ta wersja jest przydatna przy testowaniu praw istnienie i dostępu do pliku.

`m_attribute` Członkiem `CFileStatus` struktury odwołuje się do zestawu atrybutów pliku. `CFile` Klasa udostępnia **atrybut** typ wyliczania, dzięki czemu można określić symbolicznie atrybutów pliku:

```
enum Attribute {
    normal =    0x00,
    readOnly =  0x01,
    hidden =    0x02,
    system =    0x04,
    volume =    0x08,
    directory = 0x10,
    archive =   0x20
    };
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#10](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_6.cpp)]

##  <a name="hfilenull"></a>  CFile::hFileNull

Określa obecność uchwyt prawidłowego pliku dla `CFile` obiektu.

```
static AFX_DATA const HANDLE hFileNull;
```

### <a name="remarks"></a>Uwagi

Stała jest używana do określenia, czy `CFile` obiekt ma uchwyt prawidłowego pliku.

W poniższym przykładzie pokazano tej operacji:

[!code-cpp[NVC_MFCFiles#22](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_7.cpp)]

##  <a name="lockrange"></a>  CFile::LockRange

Blokuje zakresu bajtów w otwartego pliku, zostanie zgłoszony wyjątek, jeśli plik jest już zablokowany.

```
virtual void LockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>Parametry

*dwPos*<br/>
Przesunięcie w bajtach od początku zakresu bajtów do blokowania.

*dwCount*<br/>
Liczba bajtów w zakresie do zablokowania.

### <a name="remarks"></a>Uwagi

Blokowanie bajtów w pliku uniemożliwia dostęp do tych bajtów przez inne procesy. Możesz zablokować więcej niż jeden region pliku, ale nie nakładających się regiony są dozwolone.

Gdy odblokujesz regionów, przy użyciu `UnlockRange` funkcji członkowskiej, zakres bajtów musi dokładnie odpowiadać elementowi region, który wcześniej został zablokowany. `LockRange` Funkcji nie scalania sąsiadujących regionów. Jeśli sąsiadujących ze sobą dwa regiony zablokowane każdego regionu, musisz odblokować oddzielnie.

> [!NOTE]
>  Ta funkcja jest niedostępna dla `CMemFile`-klasy pochodnej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

##  <a name="m_hfile"></a>  CFile::m_hFile

Zawiera dojście do pliku systemu operacyjnego dla otwartego pliku.

```
HANDLE m_hFile;
```

### <a name="remarks"></a>Uwagi

`m_hFile` jest publiczną zmienną typu UINT. Zawiera on `CFile::hFileNull`, wskaźnik operacyjnych systemu-niezależny od pustego pliku, jeśli uchwyt nie została przypisana.

Korzystanie z `m_hFile` nie jest zalecane, ponieważ znaczenie elementu członkowskiego zależy od klasy pochodnej. `m_hFile` Wykonano publicznej składowej dla wygody w obsłudze niepolimorficznych, użyj klasy.

##  <a name="m_ptm"></a>  CFile::m_pTM

Wskaźnik do `CAtlTransactionManager` obiektu.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Uwagi

##  <a name="open"></a>  CFile::Open

Przeciążone. `Open` jest przeznaczony do użytku przy użyciu domyślnego `CFile` konstruktora.

```
virtual BOOL Open(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CAtlTransactionManager* pTM,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>Parametry

*lpszFileName*<br/>
Ciąg, który zawiera ścieżkę do pliku. Ścieżka może być względny, bezwzględne lub nazwę sieciową (UNC).

*nOpenFlags*<br/>
UINT, który definiuje tryb udostępniania i dostępu do tego pliku. Określa akcję wykonywaną podczas otwierania pliku. Opcje można połączyć za pomocą bitowej OR ( **&#124;** ) — operator. Uprawnienie dostępu jednego i jeden udział opcji są wymagane; `modeCreate` i `modeNoInherit` tryby są opcjonalne. Zobacz [CFile](#cfile) konstruktora, aby uzyskać listę opcji w trybie.

*pError*<br/>
Wskaźnik do istniejącego obiektu wyjątku plików, który zostanie wyświetlony stan operacji zakończonej niepowodzeniem.

*pTM*<br/>
Wskaźnik do obiektu CAtlTransactionManager

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli Otwórz powiodła się. w przeciwnym razie 0. *PError* parametr ma znaczenie tylko wtedy, gdy zwracany jest 0.

### <a name="remarks"></a>Uwagi

Dwa `Open` funkcje są "bezpieczne" metod do otwierania pliku, gdzie błędu jest to normalne, oczekiwane.

Gdy `CFile` Konstruktor zgłasza wyjątek w warunek błędu `Open` zwraca wartość FALSE dla warunków błędu. `Open` nadal można zainicjować [CFileException](../../mfc/reference/cfileexception-class.md) obiektu w celu opisania błędu, jednak. Jeśli nie podasz *pError* parametr, lub jeśli przekazujesz o wartości NULL dla *pError*, `Open` zwraca wartość FALSE, a nie wyrzuca `CFileException`. W przypadku przekazania wskaźnika do istniejącego `CFileException`, i `Open` napotka błąd, funkcja wypełnia go przy użyciu informacji opisujących tego błędu. `Open` nie zgłasza wyjątku w obu przypadkach.

W poniższej tabeli opisano możliwe wyniki `Open`.

|`pError`|Wystąpił błąd|Wartość zwracana|Zawartość CFileException|
|--------------|------------------------|------------------|----------------------------|
|NULL|Nie|WARTOŚĆ TRUE|n/d|
|wskaźnika `CFileException`|Nie|WARTOŚĆ TRUE|bez zmian|
|NULL|Tak|FAŁSZ|n/d|
|wskaźnika `CFileException`|Tak|FAŁSZ|zainicjowana w celu opisania błędu|

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#13](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_9.cpp)]

[!code-cpp[NVC_MFCFiles#14](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_10.cpp)]

##  <a name="operator_handle"></a>  CFile::operator UCHWYTU

Użyj tego operatora, aby przekazać dojścia do `CFile` obiektu do funkcji, takich jak [ReadFileEx](/windows/desktop/api/fileapi/nf-fileapi-readfileex) i [funkcji GetFileTime](/windows/desktop/api/fileapi/nf-fileapi-getfiletime) który oczekiwać `HANDLE`.

```
operator HANDLE() const;
```

##  <a name="read"></a>  CFile::Read

Odczytuje dane do bufora z pliku skojarzone z `CFile` obiektu.

```
virtual UINT Read(
    void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Parametry

*lpBuf*<br/>
Wskaźnik do buforu dostarczone przez użytkownika, który ma odbierać dane odczytane z pliku.

*nCount*<br/>
Maksymalna liczba bajtów do odczytu z pliku. Pliki trybu tekstowego pary wysuwu wiersza powrotu karetki są liczone jako pojedyncze znaki.

### <a name="return-value"></a>Wartość zwracana

Liczba bajtów przesłanych w buforze. Dla wszystkich `CFile` klas, zwracana wartość może być mniejsza niż *nCount* jeśli osiągnięto koniec pliku.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#15](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_11.cpp)]

Inny przykład, zobacz [CFile::Open](#open).

##  <a name="remove"></a>  CFile::Remove

Ta funkcja statyczna usuwa plik określony przez ścieżkę.

```
static void PASCAL Remove(
    LPCTSTR lpszFileName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*lpszFileName*<br/>
Ciąg, który jest ścieżka do żądanego pliku. Ścieżka może być względna lub bezwzględna i może zawierać nazwę sieci.

*pTM*<br/>
Wskaźnik do obiektu CAtlTransactionManager

### <a name="remarks"></a>Uwagi

`Remove` nie usunąć katalog.

`Remove` Funkcja elementu członkowskiego zgłasza wyjątek, jeśli połączone plik jest otwarty lub jeśli nie można usunąć pliku. Ta funkcja jest odpowiednikiem polecenia DEL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#17](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_12.cpp)]

##  <a name="rename"></a>  CFile::Rename

Ta funkcja statyczna zmienia nazwę określonego pliku.

```
static void PASCAL Rename(
    LPCTSTR lpszOldName,
    LPCTSTR lpszNewName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*lpszOldName*<br/>
Starej ścieżki.

*lpszNewName*<br/>
Nowa ścieżka.

*pTM*<br/>
Wskaźnik do obiektu CAtlTransactionManager

### <a name="remarks"></a>Uwagi

Nie można zmienić nazwy katalogów. Ta funkcja jest odpowiednikiem polecenia REN.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#18](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_13.cpp)]

##  <a name="seek"></a>  CFile::Seek

Powoduje przeniesienie wskaźnika pliku w otwartego pliku.

```
virtual ULONGLONG Seek(
LONGLONG lOff,
UINT nFrom);
```

### <a name="parameters"></a>Parametry

*lOff*<br/>
Liczba bajtów do przesuwania wskaźnika pliku. Wartości dodatnich, przesuń wskaźnik pliku pod koniec pliku. wartości ujemne Przesuń wskaźnik pliku na początku pliku.

*nFrom*<br/>
Położenie do wyszukania z. Zobacz sekcję Spostrzeżenia, aby możliwe wartości.

### <a name="return-value"></a>Wartość zwracana

Pozycja wskaźnika pliku, jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość zwracana jest niezdefiniowane i wskaźnik `CFileException` wyjątku.

### <a name="remarks"></a>Uwagi

Poniższa tabela zawiera listę możliwych wartości dla *nZe* parametru.

|Wartość|Opis|
|-----------|-----------------|
|`CFile::begin`|Wyszukiwanie od początku pliku.|
|`CFile::current`|Wyszukiwanie od bieżącej lokalizacji wskaźnika pliku.|
|`CFile::end`|Wyszukiwanie od końca pliku.|

Po otwarciu pliku wskaźnika pliku znajduje się w lokalizacji 0, na początku pliku.

Wskaźnik pliku można ustawić na pozycji poza końcem pliku. Jeśli to zrobisz, rozmiar pliku nie zwiększyć, dopóki nie można zapisać do pliku.

Po przetworzeniu wyjątek, program obsługi wyjątków dla tej metody należy usunąć obiekt wyjątku.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#9](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_14.cpp)]

##  <a name="seektobegin"></a>  CFile::SeekToBegin

Ustawia wartość wskaźnika pliku na początku pliku.

```
void SeekToBegin();
```

### <a name="remarks"></a>Uwagi

`SeekToBegin()` jest odpowiednikiem `Seek( 0L, CFile::begin )`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]

##  <a name="seektoend"></a>  CFile::SeekToEnd

Ustawia wartość wskaźnika pliku logicznego koniec pliku.

```
ULONGLONG SeekToEnd();
```

### <a name="return-value"></a>Wartość zwracana

Długość pliku w bajtach.

### <a name="remarks"></a>Uwagi

`SeekToEnd()` jest odpowiednikiem `CFile::Seek( 0L, CFile::end )`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]

##  <a name="setfilepath"></a>  CFile::SetFilePath

Wywołaj tę funkcję, aby określić ścieżkę pliku. Na przykład, jeśli ścieżka pliku jest niedostępna, gdy [CFile](../../mfc/reference/cfile-class.md) obiekt jest konstruowany, wywołaj `SetFilePath` do tego celu.

```
virtual void SetFilePath(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>Parametry

*lpszNewName*<br/>
Wskaźnik na ciąg określający nową ścieżkę.

### <a name="remarks"></a>Uwagi

> [!NOTE]
> `SetFilePath` Otwórz plik lub nie utworzony plik. po prostu kojarzy `CFile` obiektu o nazwie ścieżki, które następnie mogą być używane.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#20](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_16.cpp)]

##  <a name="setlength"></a>  CFile::SetLength

Wywołaj tę funkcję, aby zmienić długość pliku.

```
virtual void SetLength(ULONGLONG dwNewLen);
```

### <a name="parameters"></a>Parametry

*dwNewLen*<br/>
Żądana długość pliku w bajtach. Ta wartość może być większa lub mniejsza niż bieżąca długość pliku. Plik zostanie rozszerzony lub obcięte odpowiednio.

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Za pomocą `CMemFile`, ta funkcja może zgłosić `CMemoryException` obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#11](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_17.cpp)]

##  <a name="setstatus"></a>  CFile::SetStatus

Umożliwia ustawienie stanu plików skojarzonych z tej lokalizacji pliku.

```
static void PASCAL SetStatus(
    LPCTSTR lpszFileName,
    const CFileStatus& status,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*lpszFileName*<br/>
Ciąg, który jest ścieżka do żądanego pliku. Ścieżka może być względna lub bezwzględna i może zawierać nazwę sieci.

*status*<br/>
Bufor zawierającego nowe informacje o stanie. Wywołaj `GetStatus` funkcja elementu członkowskiego, aby wstępnie `CFileStatus` struktury z bieżących wartości, a następnie wprowadzić zmiany, zgodnie z potrzebami. Jeśli wartość wynosi 0, odpowiadający mu element stanu nie są aktualizowane. Zobacz [GetStatus](#getstatus) funkcja elementu członkowskiego, aby uzyskać opis `CFileStatus` struktury.

*pTM*<br/>
Wskaźnik do obiektu CAtlTransactionManager

### <a name="remarks"></a>Uwagi

Aby ustawić czas, należy zmodyfikować `m_mtime` pole *stan*.

Po ustawieniu wywołania `SetStatus` w celu podjęcia próby zmiany atrybutów pliku, a `m_mtime` elementu członkowskiego struktury stanu plików jest różna od zera, atrybuty mogą dotyczyć także (zmiana czasu sygnatury może mieć efekty uboczne atrybutów). Jeśli chcesz zmienić tylko atrybuty pliku, najpierw ustawić `m_mtime` członka struktury stanu plików do zera, a następnie wywołania `SetStatus`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#21](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_18.cpp)]

##  <a name="unlockrange"></a>  CFile::UnlockRange

Odblokowuje zakresu bajtów w otwartego pliku.

```
virtual void UnlockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>Parametry

*dwPos*<br/>
Przesunięcie w bajtach od początku zakresu bajtów, aby odblokować.

*dwCount*<br/>
Liczba bajtów w zakresie, aby odblokować.

### <a name="remarks"></a>Uwagi

Zobacz opis [LockRange](#lockrange) funkcja elementu członkowskiego, aby uzyskać szczegółowe informacje.

> [!NOTE]
>  Ta funkcja nie jest dostępna dla `CMemFile`-klasy pochodnej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

##  <a name="write"></a>  CFile::Write

Zapisuje dane z buforu do pliku związanego z `CFile` obiektu.

```
virtual void Write(
    const void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Parametry

*lpBuf*<br/>
Wskaźnik do buforu dostarczone przez użytkownika, który zawiera dane są zapisywane w pliku.

*nCount*<br/>
Liczba bajtów, które mają zostać przeniesione z buforu. Pliki trybu tekstowego pary wysuwu wiersza powrotu karetki są liczone jako pojedyncze znaki.

### <a name="remarks"></a>Uwagi

`Write` zgłasza wyjątek w odpowiedzi na kilka warunków, w tym warunku pełnego dysku.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCFiles#16](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_19.cpp)]

Zobacz też z przykładami [CFile::CFile](#cfile) i [CFile::Open](#open).

## <a name="see-also"></a>Zobacz także

[Próbki MFC DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CStdioFile](../../mfc/reference/cstdiofile-class.md)<br/>
[Klasa CMemFile](../../mfc/reference/cmemfile-class.md)
