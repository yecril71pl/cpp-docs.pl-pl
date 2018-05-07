---
title: Cfile — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ee4086b25fe675aaab1b484f21ec7e22e5603781
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cfile-class"></a>Cfile — klasa
Klasa podstawowa dla klasy plików MFC.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CFile : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFile::CFile](#cfile)|Konstruuje `CFile` obiektu dojścia ścieżki lub pliku.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFile::Abort](#abort)|Zamyka plik ignoruje wszystkie ostrzeżenia i błędy.|  
|[CFile::Close](#close)|Zamyka plik i usuwa obiekt.|  
|[CFile::Duplicate](#duplicate)|Tworzy obiekt zduplikowanych na podstawie tego pliku.|  
|[CFile::Flush](#flush)|Liczba opróżnień danych jeszcze do zapisania.|  
|[CFile::GetFileName](#getfilename)|Pobiera nazwę wybranego pliku.|  
|[CFile::GetFilePath](#getfilepath)|Pobiera pełną ścieżkę wybranego pliku.|  
|[CFile::GetFileTitle](#getfiletitle)|Pobiera tytuł wybranego pliku.|  
|[CFile::GetLength](#getlength)|Pobiera długość pliku.|  
|[CFile::GetPosition](#getposition)|Pobiera bieżącego wskaźnika pliku.|  
|[CFile::GetStatus](#getstatus)|Pobiera stan otwartego pliku, lub w wersji statycznej, pobiera stan określonego pliku (funkcja statyczna i wirtualnych).|  
|[CFile::LockRange](#lockrange)|Blokuje zakresu bajtów w pliku.|  
|[CFile::Open](#open)|Bezpiecznie otwiera plik z opcją testowania błędu.|  
|[CFile::Read](#read)|Odczytuje dane (niebuforowane) z pliku w bieżącym położeniu plików.|  
|[CFile::Remove](#remove)|Usuwa określony plik (statycznej funkcji).|  
|[CFile::Rename](#rename)|Zmienia nazwę pliku (statycznej funkcji).|  
|[CFile::Seek](#seek)|Określa położenie bieżącego wskaźnika pliku.|  
|[CFile::SeekToBegin](#seektobegin)|Określa położenie bieżącego wskaźnika pliku na początku pliku.|  
|[CFile::SeekToEnd](#seektoend)|Określa położenie bieżącego wskaźnika pliku na końcu pliku.|  
|[CFile::SetFilePath](#setfilepath)|Ustawia ścieżkę pliku pełne wybranego pliku.|  
|[CFile::SetLength](#setlength)|Zmienia długość pliku.|  
|[CFile::SetStatus](#setstatus)|Ustawia stan określonego pliku (funkcja statyczna i wirtualnych).|  
|[CFile::UnlockRange](#unlockrange)|Umożliwia odblokowanie zakresu bajtów w pliku.|  
|[CFile::Write](#write)|Zapisuje dane (niebuforowane) w pliku do bieżącego położenia pliku.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFile::operator dojścia](#operator_handle)|Dojście do `CFile` obiektu.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFile::hFileNull](#hfilenull)|Określa, czy `CFile` obiekt ma nieprawidłowy uchwyt.|  
|[CFile::m_hFile](#m_hfile)|Zwykle zawiera dojście do pliku systemu operacyjnego.|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFile::m_pTM](#m_ptm)|Wskaźnik do `CAtlTransactionManager` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Bezpośrednio udostępnia usługi wejścia/wyjścia dysku Niebuforowane, binary oraz pośrednio obsługuje pliki tekstowe i pliki pamięci za pomocą jej klas pochodnych. `CFile` działa w połączeniu z `CArchive` klasy do obsługi serializacji obiektów MFC.  
  
 Program do działania na wszystkich obiektach pliku za pośrednictwem polimorficznych umożliwia hierarchiczną relację między tej klasy i jej klas pochodnych `CFile` interfejsu. Plik pamięci, na przykład zachowuje się jak pliku na dysku.  
  
 Użyj `CFile` i jej klas pochodnych dla ogólnego przeznaczenia we/wy dysku. Użyj `ofstream` lub innych klasach iostream firmy Microsoft dla tekstu sformatowanego wysyłane do pliku na dysku.  
  
 Zazwyczaj pliku na dysku jest otwarty automatycznie na `CFile` konstruowania i zamknięte na zniszczenie. Statyczne funkcje Członkowskie pozwala przejrzeć stan pliku bez konieczności otwierania pliku.  
  
 Aby uzyskać więcej informacji na temat używania `CFile`, zobacz artykuły [pliki w MFC](../../mfc/files-in-mfc.md) i [Obsługa plików](../../c-runtime-library/file-handling.md) w *odwołanie do biblioteki wykonawczej*.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CFile`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h  
  
##  <a name="abort"></a>  CFile::Abort  
 Zamyka pliku skojarzone z tym obiektem i sprawia, że plik jest niedostępny dla operacji odczytu lub zapisu.  
  
```  
virtual void Abort();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli plik nie został zamknięty przed niszczenie obiektu, destruktor zamyka dla Ciebie.  
  
 Podczas obsługi wyjątków, `CFile::Abort` różni się od `CFile::Close` na dwa sposoby ważne. Najpierw **przerwać** funkcja nie spowoduje zgłoszenie wyjątku na awarie ponieważ błędy są ignorowane przez **przerwania**. Drugi, **przerwać** nie **ASSERT** Jeśli plik nie został otwarty lub została wcześniej zamknięta.  
  
 Jeśli używasz **nowe** przydzielić `CFile` obiektów na stercie, następnie należy ją usunąć po zamknięciu pliku. **Przerwij** ustawia `m_hFile` do `CFile::hFileNull`.  
  
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
 `hFile`  
 Dojście do pliku, aby dołączyć do `CFile` obiektu.  
  
 `lpszFileName`  
 Względna lub pełną ścieżkę do pliku do dołączenia do `CFile` obiektu.  
  
 `nOpenFlags`  
 Bitowe połączenie (lub) opcje dostępu do pliku dla określonego pliku. W sekcji uwag możliwe opcje.  
  
 `pTM`  
 Wskaźnik do obiektu CAtlTransactionManager  
  
### <a name="remarks"></a>Uwagi  
 W poniższych tabelach pięć przedstawiono możliwe opcje `nOpenFlags` parametru.  
  
 Wybierz tylko jeden z następujących opcji trybu dostępu do pliku. Jest to domyślny tryb dostępu do pliku `CFile::modeRead`, który jest tylko do odczytu.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`CFile::modeRead`|Żądania dostęp tylko do odczytu.|  
|`CFile::modeWrite`|Żądania dostępu do zapisu tylko.|  
|`CFile::modeReadWrite`|Żądania odczytu i zapisu.|  
  
 Wybierz jedną z następujących opcji trybu znaków.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`CFile::typeBinary`|Ustawia trybie binarnym (używane w klasach pochodnych tylko).|  
|`CFile::typeText`|Ustawia tryb tekstu z specjalnego przetwarzania dla pary wysuwu wiersza powrotu karetki (używane w klasach pochodnych tylko).|  
|`CFile::typeUnicode`|Ustawia tryb Unicode (używane w klasach pochodnych tylko). Tekst jest pisany w pliku w formacie Unicode, gdy aplikacja korzysta z wbudowanej w konfiguracji Unicode. Nie BOM są zapisywane do pliku.|  
  
 Wybierz tylko jeden z następujących opcji trybu udziału plików. Jest to domyślny tryb udziału pliku `CFile::shareExclusive`, który jest na wyłączność.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`CFile::shareDenyNone`|Brak ograniczeń udostępniania.|  
|`CFile::shareDenyRead`|Nie zezwala na dostęp do odczytu do wszystkich innych użytkowników.|  
|`CFile::shareDenyWrite`|Nie zezwala na dostęp do zapisu dla wszystkich innych użytkowników.|  
|`CFile::shareExclusive`|Uprawnienie odczytu i zapisu do wszystkich innych użytkowników.|  
  
 Wybierz pierwszy lub obu z następujących opcji trybu tworzenia pliku. Jest to domyślny tryb tworzenia `CFile::modeNoTruncate`, która jest Otwórz istniejący.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`CFile::modeCreate`|Tworzy nowy plik, jeśli plik nie istnieje.; Jeśli plik już istnieje, [CFileException](../../mfc/reference/cfileexception-class.md) jest wywoływane.|  
|`CFile::modeNoTruncate`|Tworzy nowy plik, jeśli plik nie istnieje; w przeciwnym razie, jeśli plik już istnieje, jest on dołączony do `CFile` obiektu.|  
  
 Wybierz plik następujące opcje buforowania, zgodnie z opisem. Domyślnie system używa ogólnego przeznaczenia pamięci podręcznej schematu, która nie jest dostępna jako opcja.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`CFile::osNoBuffer`|System nie używa pliku pośredniego pamięci podręcznej. Ta opcja umożliwia anulowanie następujące opcje 2.|  
|`CFile::osRandomAccess`|Pamięć podręczna plików jest zoptymalizowana pod kątem dostępie. Nie należy używać tej opcji i opcji sekwencyjnych skanów.|  
|`CFile::osSequentialScan`|Pamięć podręczna plików jest zoptymalizowana pod kątem dostęp sekwencyjny. Nie należy używać tej opcji i opcję dostępie.|  
|`CFile::osWriteThrough`|Operacje są wykonywane bez opóźnień zapisu.|  
  
 Wybierz następującą opcję zabezpieczeń, aby zapobiec dziedziczone przez dojście do pliku. Domyślnie wszystkie nowe procesy podrzędne można użyć dojście do pliku.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`CFile::modeNoInherit`|Wszystkie procesy podrzędne zapobiega użyciu dojście do pliku.|  
  
 Konstruktor domyślny inicjuje członków, ale nie dołączyć plik do `CFile` obiektu. Po użyciu tego konstruktora, użyj [CFile::Open](#open) metody w celu otwarcia pliku i dołączenie go do `CFile` obiektu.  
  
 Konstruktora z jednym parametrem inicjuje elementy członkowskie i dołącza do istniejącego pliku `CFile` obiektu.  
  
 Konstruktor z dwoma parametrami inicjuje elementy członkowskie i spróbuje otworzyć określonego pliku. Jeśli ten konstruktor pomyślnie otwiera określony plik, plik jest dołączony do `CFile` obiektu; w przeciwnym razie ten konstruktor zwraca wskaźnik do `CInvalidArgException` obiektu. Aby uzyskać więcej informacji na temat obsługi wyjątków, zobacz [wyjątki](../../mfc/exception-handling-in-mfc.md).  
  
 Jeśli `CFile` obiektu pomyślnie otwiera określony plik, zostanie on zamknięty ten plik automatycznie po `CFile` obiektu; w przeciwnym razie należy jawnie zamknąć plik po nie jest już dołączony do `CFile` obiektu.  
  
### <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób użycia `CFile`.  
  
 [!code-cpp[NVC_MFCFiles#4](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_2.cpp)]  
  
##  <a name="close"></a>  CFile::Close  
 Zamyka pliku skojarzone z tym obiektem i sprawia, że plik jest niedostępny dla operacji odczytu lub zapisu.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Uwagi  
 Jeśli plik nie został zamknięty przed niszczenie obiektu, destruktor zamyka dla Ciebie.  
  
 Jeśli używasz **nowe** przydzielić `CFile` obiektów na stercie, następnie należy ją usunąć po zamknięciu pliku. **Zamknij** ustawia `m_hFile` do `CFile::hFileNull`.  
  
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
 Odpowiada to funkcji wykonawcze języka C `_dup`.  
  
##  <a name="flush"></a>  CFile::Flush  
 Wymusza żadnych danych pozostałych w buforze pliku do zapisania do pliku.  
  
```  
virtual void Flush();
```  
  
### <a name="remarks"></a>Uwagi  
 Korzystanie z `Flush` nie gwarantuje opróżnianie z `CArchive` buforów. Jeśli używasz archiwum wywołanie [CArchive::Flush](../../mfc/reference/carchive-class.md#flush) pierwszy.  
  
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
 Na przykład podczas wywoływania `GetFileName` można wygenerować komunikatu dla użytkownika o pliku `c:\windows\write\myfile.wri`, nazwa pliku, `myfile.wri`, jest zwracany.  
  
 Aby powrócić na całej ścieżce pliku, w tym nazwę, wywołanie [GetFilePath](#getfilepath). Aby przywrócić nazwy pliku ( `myfile`), wywołaj [GetFileTitle](#getfiletitle).  
  
### <a name="example"></a>Przykład  
 Fragmentu kodu otwiera SYSTEM. Plik INI w katalogu systemu WINDOWS. Jeśli znaleziono przykładzie będzie drukować nazwę i ścieżkę i tytułu, jak pokazano w danych wyjściowych:  
  
 [!code-cpp[NVC_MFCFiles#6](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_3.cpp)]  
  
##  <a name="getfilepath"></a>  CFile::GetFilePath  
 Wywołanie tej funkcji Członkowskich pobrać pełną ścieżkę określonego pliku.  
  
```  
virtual CString GetFilePath() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Pełna ścieżka pliku.  
  
### <a name="remarks"></a>Uwagi  
 Na przykład podczas wywoływania `GetFilePath` można wygenerować komunikatu dla użytkownika o pliku `c:\windows\write\myfile.wri`, ścieżkę pliku `c:\windows\write\myfile.wri`, jest zwracany.  
  
 Aby zwracać tylko nazwę pliku ( `myfile.wri`), wywołaj [GetFileName](#getfilename). Aby przywrócić nazwy pliku ( `myfile`), wywołaj [GetFileTitle](#getfiletitle).  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [GetFileName](#getfilename).  
  
##  <a name="getfiletitle"></a>  CFile::GetFileTitle  
 Wywołanie tej funkcji członkowskich można pobrać nazwy pliku (nazwa wyświetlana) dla pliku.  
  
```  
virtual CString GetFileTitle() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Nazwa pliku źródłowego.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wywołuje [GetFileTitle](http://msdn.microsoft.com/library/windows/desktop/ms646924) można pobrać nazwy pliku. Jeśli to się powiedzie, metoda zwraca ciąg, który system użyje, aby wyświetlić nazwę pliku dla użytkownika. W przeciwnym razie wywołuje metodę [PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589) pobrać nazwy pliku (w tym rozszerzenia pliku) pliku źródłowego. W związku z tym rozszerzeniem pliku zostanie nie zawsze uwzględniane w ciągu tytuł zwrócony pliku. Aby uzyskać więcej informacji, zobacz [GetFileTitle](http://msdn.microsoft.com/library/windows/desktop/ms646924) i [PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589) w zestawie Windows SDK.  
  
 Aby powrócić na całej ścieżce pliku, w tym nazwę, wywołanie [GetFilePath](#getfilepath). Aby zwracać tylko nazwę pliku, należy wywołać [GetFileName](#getfilename).  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [GetFileName](#getfilename).  
  
##  <a name="getlength"></a>  CFile::GetLength  
 Pobiera bieżącą logicznej długość pliku w bajtach.  
  
```  
virtual ULONGLONG GetLength() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Długość pliku.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCFiles#7](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_4.cpp)]  
  
##  <a name="getposition"></a>  CFile::GetPosition  
 Pobiera bieżącą wartość wskaźnika pliku, którego można użyć w kolejnych wywołaniach `Seek`.  
  
```  
virtual ULONGLONG GetPosition() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnika pliku.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCFiles#8](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_5.cpp)]  
  
##  <a name="getstatus"></a>  CFile::GetStatus  
 Ta metoda pobiera informacje o stanie związane z danym `CFile` wystąpienie obiektu lub ścieżka danego pliku.  
  
```  
BOOL GetStatus(CFileStatus& rStatus) const;  
  
static BOOL PASCAL GetStatus(
    LPCTSTR lpszFileName,  
    CFileStatus& rStatus,
    CAtlTransactionManager* pTM = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `rStatus`  
 Odwołanie do podanego użytkownika **CFileStatus** struktury, które będą otrzymywać informacje o stanie. **CFileStatus** struktury ma następujące pola:  
  
- **Ctime — m_ctime** Data i godzina utworzenia pliku.  
  
- **Ctime — m_mtime** datę i godzinę ostatniej modyfikacji pliku.  
  
- **Ctime — m_atime** Data i godzina ostatniego dostępu do pliku do odczytu.  
  
- **ULONGLONG m_size** rozmiaru logicznego pliku w bajtach, jak za pomocą polecenia DIR.  
  
- **M_attribute BAJTÓW** bajt atrybut pliku.  
  
- **CHAR — m_szFullName [_max_path —]** bezwzględnej nazwy pliku w zestawie znaków systemu Windows.  
  
 `lpszFileName`  
 Ciąg znaków Windows oznacza to ustawić ścieżkę do pliku. Ścieżka może być względna lub bezwzględna lub może zawierać nazwę ścieżki sieciowej.  
  
 `pTM`  
 Wskaźnik do obiektu CAtlTransactionManager  
  
### <a name="return-value"></a>Wartość zwracana  
 **Wartość TRUE,** Jeśli informacje o stanie dla określonego pliku zostanie pomyślnie uzyskanych; w przeciwnym razie **FALSE**.  
  
### <a name="remarks"></a>Uwagi  
 Wersja niestatyczna **GetStatus** pobiera informacje o stanie otwartego pliku skojarzone z danym `CFile` obiektu.  W wersji statycznej **GetStatus** uzyskuje stan pliku z danej ścieżce bez konieczności otwierania pliku. Jest to przydatna przy testowaniu prawa istnienia i dostępu do pliku.  
  
 **M_attribute** członkiem **CFileStatus** struktury odwołuje się do zestawu atrybutów pliku. `CFile` Klasa udostępnia **atrybutu** wyliczenie wpisz tak atrybutów plików można określić symbolicznie:  
  
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
 Określa obecności uchwyt prawidłowy plik dla `CFile` obiektu.  
  
```  
static AFX_DATA const HANDLE hFileNull;  
```  
  
### <a name="remarks"></a>Uwagi  
 Stała ta służy do określenia, czy `CFile` obiekt ma uchwyt prawidłowy plik.  
  
 W poniższym przykładzie pokazano tej operacji:  
  
 [!code-cpp[NVC_MFCFiles#22](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_7.cpp)]  
  
##  <a name="lockrange"></a>  CFile::LockRange  
 Blokuje zakresu bajtów, w której plik otwarty zgłoszeniu wyjątku, jeśli plik jest już zablokowany.  
  
```  
virtual void LockRange(
    ULONGLONG dwPos,  
    ULONGLONG dwCount);
```  
  
### <a name="parameters"></a>Parametry  
 `dwPos`  
 Przesunięcie bajtów początek zakresu bajtów do zablokowania.  
  
 `dwCount`  
 Liczba bajtów w zakresie do zablokowania.  
  
### <a name="remarks"></a>Uwagi  
 Blokowanie bajtów w pliku uniemożliwia dostęp do tych bajtów przez inne procesy. Można zablokować więcej niż jeden region, pliku, ale nie nakładające się regiony są dozwolone.  
  
 Po odblokowaniu region przy użyciu `UnlockRange` funkcji członkowskiej zakres bajtów musi odpowiadać dokładnie region, który wcześniej był zablokowany. `LockRange` Funkcja scalania nie sąsiadujących ze sobą regionów; Jeśli dwóch regionach zablokowanym sąsiadujących ze sobą, musisz odblokować każdego regionu oddzielnie.  
  
> [!NOTE]
>  Ta funkcja nie jest dostępna dla `CMemFile`-klasy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]  
  
##  <a name="m_hfile"></a>  CFile::m_hFile  
 Zawiera dojście do pliku systemu operacyjnego dla otwartego pliku.  
  
```  
HANDLE m_hFile;  
```  
  
### <a name="remarks"></a>Uwagi  
 `m_hFile` jest publiczny zmiennej typu **UINT**. Zawiera on `CFile::hFileNull` (wskaźnik działania systemu-niezależne od pusty plik) Jeśli dojście nie został przypisany.  
  
 Użycie `m_hFile` nie jest zalecane, ponieważ element członkowski znaczenie zależy od klasy pochodnej. `m_hFile` następuje publicznego elementu członkowskiego dla wygody w obsługi nonpolymorphic Użyj klasy.  
  
##  <a name="m_ptm"></a>  CFile::m_pTM  
 Wskaźnik do `CAtlTransactionManager` obiektu.  
  
```  
CAtlTransactionManager* m_pTM;  
```  
  
### <a name="remarks"></a>Uwagi  
  
##  <a name="open"></a>  CFile::Open  
 Przeciążone. **Otwórz** jest przeznaczony do użytku z domyślnym `CFile` konstruktora.  
  
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
 `lpszFileName`  
 Ciąg, który jest ścieżka do żądanego pliku. Ścieżka może być względna, bezwzględna lub nazwa sieciowa (UNC).  
  
 `nOpenFlags`  
 A **UINT** definiuje tryb dostępu i udostępniania plików. Określa akcję wykonywaną podczas otwierania pliku. Opcje można połączyć za pomocą wartości bitowe lub ( **&#124;** ) operatora. Opcji jednego udziału i uprawnień dostępu co są wymagane; **modeCreate** i **modeNoInherit** tryby są opcjonalne. Zobacz [cfile —](#cfile) konstruktora, aby uzyskać listę opcji trybu.  
  
 `pError`  
 Wskaźnik do istniejącego obiektu wyjątku plików, który zostanie wyświetlony stan operacji nie powiodło się.  
  
 `pTM`  
 Wskaźnik do obiektu CAtlTransactionManager  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli Otwórz zakończyło się pomyślnie; w przeciwnym razie 0. `pError` Parametr ma znaczenie tylko wtedy, gdy zwracany jest 0.  
  
### <a name="remarks"></a>Uwagi  
 Dwie funkcje stanowią metodę "bezpiecznej" na potrzeby otwierania pliku, w którym awarii jest to normalne, oczekiwane.  
  
 Gdy `CFile` Konstruktor spowoduje zgłoszenie wyjątku w stanie błędu **Otwórz** zwróci **FALSE** dla warunków błędu. **Otwórz** mogą nadal zainicjować [CFileException](../../mfc/reference/cfileexception-class.md) obiektu do opisu błędu, jednak. Jeśli nie podasz `pError` parametr, lub w przypadku przekazania **NULL** dla `pError`, **Otwórz** zwróci **FALSE** i nie `CFileException`. W przypadku przekazania wskaźnik do istniejącej `CFileException`, i **Otwórz** napotka błąd, funkcja wprowadzi ona informacji na temat tego błędu. Żadna wielkość wykona **Otwórz** zgłoszenia wyjątku.  
  
 W poniższej tabeli opisano możliwe wyniki **Otwórz**.  
  
|`pError`|Wystąpił błąd|Wartość zwracana|Zawartość CFileException|  
|--------------|------------------------|------------------|----------------------------|  
|**NULL**|Nie|**WARTOŚĆ TRUE**|n/d|  
|wskaźnika `CFileException`|Nie|**WARTOŚĆ TRUE**|Bez zmian|  
|**NULL**|Tak|**WARTOŚĆ FALSE**|n/d|  
|wskaźnika `CFileException`|Tak|**WARTOŚĆ FALSE**|zainicjowano opisujący błąd|  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCFiles#13](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_9.cpp)]  
  
 [!code-cpp[NVC_MFCFiles#14](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_10.cpp)]  
  
##  <a name="operator_handle"></a>  CFile::operator dojścia  
 Użyj tego operatora, aby przekazać dojścia do `CFile` obiekt do funkcji, takich jak [ReadFileEx](http://msdn.microsoft.com/library/windows/desktop/aa365468) i [funkcji GetFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724320) który oczekiwać `HANDLE`.  
  
```  
operator HANDLE() const;  
```  
  
##  <a name="read"></a>  CFile::Read  
 Odczytuje dane w buforze z pliku skojarzone z `CFile` obiektu.  
  
```  
virtual UINT Read(
    void* lpBuf,  
    UINT nCount);
```  
  
### <a name="parameters"></a>Parametry  
 `lpBuf`  
 Wskaźnik do buforu dostarczone przez użytkownika, który będzie odbierać dane odczytane z pliku.  
  
 `nCount`  
 Maksymalna liczba bajtów do odczytu z pliku. Dla plików trybu tekstu pary wysuwu wiersza powrotu karetki są liczone jako pojedynczy znaki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba bajtów przesłanych w buforze. Należy pamiętać, że dla wszystkich `CFile` klas, zwracana wartość może być mniejsza niż `nCount` czy osiągnięto koniec pliku.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCFiles#15](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_11.cpp)]  
  
 Innym przykładem zobacz [CFile::Open](#open).  
  
##  <a name="remove"></a>  CFile::Remove  
 Ta funkcja statyczna usuwa plik określony przez ścieżkę.  
  
```  
static void PASCAL Remove(
    LPCTSTR lpszFileName, 
    CAtlTransactionManager* pTM = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFileName`  
 Ciąg, który jest ścieżka do żądanego pliku. Ścieżka może być względna lub bezwzględna i może zawierać nazwy sieci.  
  
 `pTM`  
 Wskaźnik do obiektu CAtlTransactionManager  
  
### <a name="remarks"></a>Uwagi  
 Nie spowoduje to usunięcie katalogu.  
  
 **Usuń** funkcji członkowskiej zgłasza wyjątek, jeśli połączone plik jest otwarty lub nie można usunąć pliku. Jest to równoważne polecenie DEL.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCFiles#17](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_12.cpp)]  
  
##  <a name="rename"></a>  CFile::Rename  
 Ta funkcja statyczna zmienia nazwę pliku.  
  
```  
static void PASCAL Rename(
    LPCTSTR lpszOldName,  
    LPCTSTR lpszNewName,  
    CAtlTransactionManager* pTM = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszOldName`  
 Starej ścieżki.  
  
 `lpszNewName`  
 Nowej ścieżki.  
  
 `pTM`  
 Wskaźnik do obiektu CAtlTransactionManager  
  
### <a name="remarks"></a>Uwagi  
 Nie można zmienić nazwy katalogów. Jest to równoważne polecenia REN.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCFiles#18](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_13.cpp)]  
  
##  <a name="seek"></a>  CFile::Seek  
 Zmienia położenie wskaźnika pliku, w której plik otwarty.  
  
```  
virtual ULONGLONG Seek(
LONGLONG lOff,  
UINT nFrom);
```  
  
### <a name="parameters"></a>Parametry  
 `lOff`  
 Liczba bajtów do przesuwania wskaźnika pliku. Dodatnie wartości przesunięcia wskaźnika pliku pod koniec pliku. wartości ujemne wskaźnika pliku na początku pliku.  
  
 `nFrom`  
 Położenie do wyszukania z. W sekcji uwag możliwych wartości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Pozycja wskaźnika pliku, jeśli metoda zakończyło się pomyślnie; w przeciwnym razie wartość zwracana jest niezdefiniowane i wskaźnika do `CFileException` wyjątku.  
  
### <a name="remarks"></a>Uwagi  
 W poniższej tabeli przedstawiono możliwe wartości `nFrom` parametru.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`CFile::begin`|Wyszukiwanie od początku pliku.|  
|`CFile::current`|Wyszukiwania z bieżącego położenia wskaźnika pliku.|  
|`CFile::end`|Wyszukiwanie od końca pliku.|  
  
 Po otwarciu pliku wskaźnika pliku znajduje się w lokalizacji 0, początku pliku.  
  
 Można ustawić wskaźnika pliku do położenia poza koniec pliku. Jeśli to zrobisz, nie zwiększenie rozmiaru pliku aż do zapisu w pliku.  
  
 Obsługa wyjątków dla tej metody należy usunąć obiekt wyjątku po przetworzeniu wyjątek.  
  
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
 Ustawia wartość wskaźnika plik logicznej koniec pliku.  
  
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
 Wywołanie tej funkcji, aby określić ścieżkę pliku. na przykład, jeśli ścieżka pliku jest niedostępne podczas [cfile —](../../mfc/reference/cfile-class.md) konstruowania obiektu, należy wywołać `SetFilePath` do tego celu.  
  
```  
virtual void SetFilePath(LPCTSTR lpszNewName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszNewName`  
 Wskaźnik do ciąg określający nowej ścieżki.  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> `SetFilePath` nie jego otwarcia lub utworzenia pliku; po prostu kojarzy `CFile` obiektu o nazwie ścieżki, które mogą być następnie używane.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCFiles#20](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_16.cpp)]  
  
##  <a name="setlength"></a>  CFile::SetLength  
 Wywołanie tej funkcji, aby zmienić długość pliku.  
  
```  
virtual void SetLength(ULONGLONG dwNewLen);
```  
  
### <a name="parameters"></a>Parametry  
 `dwNewLen`  
 Żądana długość pliku w bajtach. Ta wartość może być większa lub mniejsza niż bieżąca długość pliku. Plik zostanie rozszerzony lub obcięty odpowiednio.  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Z `CMemFile`, ta funkcja może wywoływać `CMemoryException` obiektu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCFiles#11](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_17.cpp)]  
  
##  <a name="setstatus"></a>  CFile::SetStatus  
 Ustawia stan pliku skojarzone z tej lokalizacji pliku.  
  
```  
static void PASCAL SetStatus(
    LPCTSTR lpszFileName,  
    const CFileStatus& status,  
    CAtlTransactionManager* pTM = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFileName`  
 Ciąg, który jest ścieżka do żądanego pliku. Ścieżka może być względna lub bezwzględna i może zawierać nazwy sieci.  
  
 *status*  
 Bufor zawierającego nowe informacje o stanie. Wywołanie **GetStatus** funkcji członkowskiej, aby wstępnie **CFileStatus** struktury bieżącymi wartościami, a następnie wprowadź wymagane zmiany. Jeśli wartość wynosi 0, odpowiadający mu element stan nie zostanie zaktualizowany. Zobacz [GetStatus](#getstatus) funkcji członkowskiej opis **CFileStatus** struktury.  
  
 `pTM`  
 Wskaźnik do obiektu CAtlTransactionManager  
  
### <a name="remarks"></a>Uwagi  
 Aby ustawić czas, należy zmodyfikować **m_mtime** pole *stan*.  
  
 Należy pamiętać, że po wprowadzeniu wywołanie `SetStatus` w celu zmiany atrybutów pliku i **m_mtime** element członkowski struktury stan pliku jest różna od zera, może również dotyczyć atrybutów (zmiana sygnatury czasowej może mieć efekty uboczne atrybutów). Jeśli chcesz zmienić tylko atrybuty pliku, najpierw ustaw **m_mtime** elementu członkowskiego struktury stanu plików na zero i następnie wywoływania `SetStatus`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCFiles#21](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_18.cpp)]  
  
##  <a name="unlockrange"></a>  CFile::UnlockRange  
 Umożliwia odblokowanie zakresu bajtów, w której plik otwarty.  
  
```  
virtual void UnlockRange(
    ULONGLONG dwPos,  
    ULONGLONG dwCount);
```  
  
### <a name="parameters"></a>Parametry  
 `dwPos`  
 Przesunięcie bajtów początek zakresu bajtów, aby odblokować.  
  
 `dwCount`  
 Liczba bajtów w zakresie, aby odblokować.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz opis [LockRange](#lockrange) funkcji członkowskiej, aby uzyskać szczegółowe informacje.  
  
> [!NOTE]
>  Ta funkcja nie jest dostępna dla `CMemFile`-klasy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]  
  
##  <a name="write"></a>  CFile::Write  
 Zapisuje dane z bufora do pliku związanego z `CFile` obiektu.  
  
```  
virtual void Write(
    const void* lpBuf,  
    UINT nCount);
```  
  
### <a name="parameters"></a>Parametry  
 `lpBuf`  
 Wskaźnik do buforu dostarczone przez użytkownika, zawierający dane są zapisywane w pliku.  
  
 `nCount`  
 Liczba bajtów do przeniesienia z buforu. Dla plików trybu tekstu pary wysuwu wiersza powrotu karetki są liczone jako pojedynczy znaki.  
  
### <a name="remarks"></a>Uwagi  
 **Zapis** zgłasza wyjątek w odpowiedzi na kilka warunków, w tym warunku pełnej dysku.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCFiles#16](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_19.cpp)]  
  
 Ponadto zawiera przykłady dla [CFile::CFile](#cfile) i [CFile::Open](#open).  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC DRAWCLI](../../visual-cpp-samples.md)   
 [CObject — klasa](../../mfc/reference/cobject-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CStdioFile](../../mfc/reference/cstdiofile-class.md)   
 [Klasa CMemFile](../../mfc/reference/cmemfile-class.md)
