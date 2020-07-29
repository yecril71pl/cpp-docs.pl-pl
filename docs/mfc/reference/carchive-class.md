---
title: Klasa CArchive
ms.date: 11/04/2016
f1_keywords:
- CArchive
- AFX/CArchive
- AFX/CArchive::CArchive
- AFX/CArchive::Abort
- AFX/CArchive::Close
- AFX/CArchive::Flush
- AFX/CArchive::GetFile
- AFX/CArchive::GetObjectSchema
- AFX/CArchive::IsBufferEmpty
- AFX/CArchive::IsLoading
- AFX/CArchive::IsStoring
- AFX/CArchive::MapObject
- AFX/CArchive::Read
- AFX/CArchive::ReadClass
- AFX/CArchive::ReadObject
- AFX/CArchive::ReadString
- AFX/CArchive::SerializeClass
- AFX/CArchive::SetLoadParams
- AFX/CArchive::SetObjectSchema
- AFX/CArchive::SetStoreParams
- AFX/CArchive::Write
- AFX/CArchive::WriteClass
- AFX/CArchive::WriteObject
- AFX/CArchive::WriteString
- AFX/CArchive::m_pDocument
helpviewer_keywords:
- CArchive [MFC], CArchive
- CArchive [MFC], Abort
- CArchive [MFC], Close
- CArchive [MFC], Flush
- CArchive [MFC], GetFile
- CArchive [MFC], GetObjectSchema
- CArchive [MFC], IsBufferEmpty
- CArchive [MFC], IsLoading
- CArchive [MFC], IsStoring
- CArchive [MFC], MapObject
- CArchive [MFC], Read
- CArchive [MFC], ReadClass
- CArchive [MFC], ReadObject
- CArchive [MFC], ReadString
- CArchive [MFC], SerializeClass
- CArchive [MFC], SetLoadParams
- CArchive [MFC], SetObjectSchema
- CArchive [MFC], SetStoreParams
- CArchive [MFC], Write
- CArchive [MFC], WriteClass
- CArchive [MFC], WriteObject
- CArchive [MFC], WriteString
- CArchive [MFC], m_pDocument
ms.assetid: 9e950d23-b874-456e-ae4b-fe00781a7699
ms.openlocfilehash: 48ed2a0edfcc17603a62e6830bf1c8d68c11932a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231900"
---
# <a name="carchive-class"></a>Klasa CArchive

Umożliwia zapisanie złożonej sieci obiektów w trwałej postaci binarnej (zazwyczaj magazynu dyskowego), która będzie trwała po usunięciu obiektów.

## <a name="syntax"></a>Składnia

```
class CArchive
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CArchive:: CArchive](#carchive)|Tworzy obiekt `CArchive`.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CArchive:: Abort](#abort)|Zamyka archiwum bez zgłaszania wyjątku.|
|[CArchive:: Close](#close)|Opróżnia niezapisywane dane i rozłącza od `CFile` .|
|[CArchive:: Flush](#flush)|Opróżnia niezapisywane dane z buforu archiwum.|
|[CArchive:: GetFile](#getfile)|Pobiera `CFile` wskaźnik obiektu dla tego archiwum.|
|[CArchive:: GetObjectSchema](#getobjectschema)|Wywoływana z `Serialize` funkcji w celu określenia wersji obiektu, który jest deserializowany.|
|[CArchive:: IsBufferEmpty](#isbufferempty)|Określa, czy bufor został opróżniony podczas procesu odbierania Windows Sockets.|
|[CArchive:: IsLoading](#isloading)|Określa, czy archiwum jest ładowane.|
|[CArchive:: isprzechowywanie](#isstoring)|Określa, czy archiwum jest przechowywane.|
|[CArchive:: MapObject](#mapobject)|Umieszcza obiekty w mapie, które nie są serializowane do pliku, ale są dostępne dla podobiektów do odwołania.|
|[CArchive:: Read](#read)|Odczytuje nieprzetworzone bajty.|
|[CArchive:: ReadClass](#readclass)|Odczytuje odwołanie do klasy poprzednio przechowywane w `WriteClass` .|
|[CArchive:: ReadObject](#readobject)|Wywołuje `Serialize` funkcję obiektu do załadowania.|
|[CArchive:: ReadString](#readstring)|Odczytuje pojedynczy wiersz tekstu.|
|[CArchive:: SerializeClass](#serializeclass)|Odczytuje lub zapisuje odwołanie klasy do obiektu w `CArchive` zależności od kierunku `CArchive` .|
|[CArchive:: SetLoadParams](#setloadparams)|Ustawia rozmiar, do którego zostanie powiększona tablica obciążenia. Musi być wywoływana przed załadowaniem dowolnego obiektu lub `MapObject` przed `ReadObject` wywołaniem lub.|
|[CArchive:: SetObjectSchema](#setobjectschema)|Ustawia schemat obiektu przechowywany w obiekcie archiwum.|
|[CArchive:: SetStoreParams](#setstoreparams)|Ustawia rozmiar tabeli skrótu i rozmiar bloku mapy używany do identyfikowania unikatowych obiektów w procesie serializacji.|
|[CArchive:: Write](#write)|Zapisuje nieprzetworzone bajty.|
|[CArchive:: WriteClass](#writeclass)|Zapisuje odwołanie do `CRuntimeClass` `CArchive` .|
|[CArchive:: WriteObject](#writeobject)|Wywołuje `Serialize` funkcję obiektu do przechowywania.|
|[CArchive:: WriteString](#writestring)|Zapisuje pojedynczy wiersz tekstu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CArchive:: operator&lt;&lt;](#operator_lt_lt)|Przechowuje obiekty i typy pierwotne w archiwum.|
|[CArchive:: operator&gt;&gt;](#operator_gt_gt)|Ładuje obiekty i typy pierwotne z archiwum.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CArchive:: m_pDocument](#m_pdocument)||

## <a name="remarks"></a>Uwagi

`CArchive`nie ma klasy bazowej.

Później można załadować obiekty z magazynu trwałego, odtworząc je w pamięci. Ten proces tworzenia trwałych danych jest nazywany "serializacji".

Obiekt archiwum można traktować jako rodzaj strumienia binarnego. Podobnie jak w przypadku strumienia danych wejściowych/wyjściowych, archiwum jest skojarzone z plikiem i pozwala na zbuforowane zapisywanie i odczytywanie danych do i z magazynu. Strumień danych wejściowych/wyjściowych przetwarza sekwencje znaków ASCII, ale archiwum przetwarza dane obiektów binarnych w wydajny, nadmiarowy format.

Aby można było utworzyć obiekt, należy utworzyć obiekt [CFile](../../mfc/reference/cfile-class.md) `CArchive` . Ponadto należy upewnić się, że stan załadowania/przechowywania archiwum jest zgodny z trybem otwartym pliku. Masz ograniczone do jednego aktywnego Archiwum na plik.

Podczas konstruowania `CArchive` obiektu, należy dołączyć go do obiektu klasy `CFile` (lub klasy pochodnej), która reprezentuje otwarty plik. Należy również określić, czy archiwum będzie używane do ładowania, czy przechowywania. `CArchive`Obiekt może przetworzyć nie tylko typy pierwotne, ale również obiekty klas pochodnych [CObject](../../mfc/reference/cobject-class.md)zaprojektowanych do serializacji. Klasa możliwa do serializacji ma zwykle `Serialize` funkcję członkowską i zwykle używa makr [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) i [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) , zgodnie z opisem w klasie `CObject` .

Przeciążone operatory wyodrębniania ( **>>** ) i wstawiania ( **<<** ) to wygodne interfejsy programowania archiwum, które obsługują zarówno typy pierwotne, jak i `CObject` klasy pochodne.

`CArchive`obsługuje także programowanie z klasami Windows Sockets MFC [CSocket](../../mfc/reference/csocket-class.md) i [CSocketFile](../../mfc/reference/csocketfile-class.md). Funkcja członkowska [IsBufferEmpty](#isbufferempty) obsługuje to użycie.

Aby uzyskać więcej informacji na temat `CArchive` , zobacz artykuł [serializacji](../../mfc/serialization-in-mfc.md) i [Windows Sockets: używanie gniazd z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CArchive`

## <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

## <a name="carchiveabort"></a><a name="abort"></a>CArchive:: Abort

Wywołaj tę funkcję, aby zamknąć archiwum bez zgłaszania wyjątku.

```cpp
void Abort ();
```

### <a name="remarks"></a>Uwagi

`CArchive`Destruktor będzie zazwyczaj wywoływany `Close` , co spowoduje opróżnienie wszystkich danych, które nie zostały zapisane w skojarzonym `CFile` obiekcie. Może to spowodować wyjątki.

Podczas przechwytywania tych wyjątków dobrym pomysłem jest użycie `Abort` , aby destruktor `CArchive` obiektu nie powodował dalszych wyjątków. Podczas obsługi wyjątków `CArchive::Abort` nie zostanie zgłoszony wyjątek w przypadku błędów, ponieważ, w przeciwieństwie do [CArchive:: Close](#close), `Abort` ignoruje błędy.

Jeśli użyto **`new`** do przydzielenia `CArchive` obiektu na stercie, należy go usunąć po zamknięciu pliku.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CArchive:: WriteClass](#writeclass).

## <a name="carchivecarchive"></a><a name="carchive"></a>CArchive:: CArchive

Konstruuje `CArchive` obiekt i określa, czy będzie on używany do ładowania lub przechowywania obiektów.

```
CArchive(
    CFile* pFile,
    UINT nMode,
    int nBufSize = 4096,
    void* lpBuf = NULL);
```

### <a name="parameters"></a>Parametry

*pFile*<br/>
Wskaźnik do `CFile` obiektu, który jest ostatecznym źródłem lub miejscem docelowym danych trwałych.

*nMode*<br/>
Flaga określająca, czy obiekty będą ładowane z lub przechowywane w archiwum. Parametr *nMode* musi mieć jedną z następujących wartości:

- `CArchive::load`Ładuje dane z archiwum. Wymaga tylko `CFile` uprawnienia do odczytu.

- `CArchive::store`Zapisuje dane w archiwum. Wymaga `CFile` uprawnień do zapisu.

- `CArchive::bNoFlushOnDelete`Uniemożliwia automatyczne wywoływanie Archiwum `Flush` po wywołaniu destruktora archiwum. Jeśli ustawisz tę flagę, użytkownik jest odpowiedzialny za jawne wywołanie `Close` przed wywołaniem destruktora. Jeśli tego nie zrobisz, Twoje dane będą uszkodzone.

*nBufSize*<br/>
Liczba całkowita określająca rozmiar wewnętrznego bufora plików (w bajtach). Należy pamiętać, że domyślny rozmiar buforu to 4 096 bajtów. W przypadku rutynowej archiwizacji dużych obiektów poprawisz wydajność, jeśli używasz większego rozmiaru buforu, który jest wielokrotnością rozmiaru buforu pliku.

*lpBuf*<br/>
Opcjonalny wskaźnik do buforu dostarczonego przez użytkownika o rozmiarze *nBufSize*. Jeśli ten parametr nie zostanie określony, archiwum przydzieli bufor ze sterty lokalnej i zwolni go, gdy obiekt zostanie zniszczony. Archiwum nie zwalnia buforu dostarczonego przez użytkownika.

### <a name="remarks"></a>Uwagi

Nie można zmienić tej specyfikacji po utworzeniu archiwum.

Nie można używać `CFile` operacji do zmiany stanu pliku do momentu zamknięcia archiwum. Każda taka operacja spowoduje uszkodzenie integralności archiwum. Możesz uzyskać dostęp do pozycji wskaźnika pliku w dowolnym momencie podczas serializacji, uzyskując obiekt pliku archiwum z funkcji elementu członkowskiego [GetFile](#getfile) , a następnie używając funkcji [CFile:: GetPosition](../../mfc/reference/cfile-class.md#getposition) . Należy wywołać metodę [CArchive:: Flush](#flush) przed uzyskaniem pozycji wskaźnika pliku.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#12](../../mfc/codesnippet/cpp/carchive-class_1.cpp)]

## <a name="carchiveclose"></a><a name="close"></a>CArchive:: Close

Opróżnia wszystkie pozostałe dane w buforze, zamyka archiwum i rozłącza archiwum z pliku.

```cpp
void Close();
```

### <a name="remarks"></a>Uwagi

Żadne dalsze operacje na archiwum nie są dozwolone. Po zamknięciu archiwum można utworzyć inne Archiwum dla tego samego pliku lub zamknąć plik.

Funkcja członkowska `Close` zapewnia, że wszystkie dane są przesyłane z archiwum do pliku i uniemożliwiają dostęp do archiwum. Aby ukończyć transfer z pliku do nośnika magazynu, należy najpierw użyć [CFile:: Close](../../mfc/reference/cfile-class.md#close) , a następnie zniszczyć `CFile` obiekt.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CArchive:: WriteString](#writestring).

## <a name="carchiveflush"></a><a name="flush"></a>CArchive:: Flush

Wymusza, aby wszystkie pozostałe dane w buforze archiwum były zapisywane do pliku.

```cpp
void Flush();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska `Flush` gwarantuje, że wszystkie dane są przesyłane z archiwum do pliku. Musisz wywołać [CFile:: Close](../../mfc/reference/cfile-class.md#close) , aby zakończyć transfer z pliku na nośnik magazynujący.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#13](../../mfc/codesnippet/cpp/carchive-class_2.cpp)]

## <a name="carchivegetfile"></a><a name="getfile"></a>CArchive:: GetFile

Pobiera `CFile` wskaźnik obiektu dla tego archiwum.

```
CFile* GetFile() const;
```

### <a name="return-value"></a>Wartość zwracana

Stały wskaźnik do `CFile` obiektu w użyciu.

### <a name="remarks"></a>Uwagi

Należy opróżnić archiwum przed użyciem `GetFile` .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#14](../../mfc/codesnippet/cpp/carchive-class_3.cpp)]

## <a name="carchivegetobjectschema"></a><a name="getobjectschema"></a>CArchive:: GetObjectSchema

Wywołaj tę funkcję z `Serialize` funkcji, aby określić wersję obiektu, który jest obecnie deserializowany.

```
UINT GetObjectSchema();
```

### <a name="return-value"></a>Wartość zwracana

Podczas deserializacji wersja obiektu jest odczytywana.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji jest prawidłowe tylko wtedy, gdy `CArchive` obiekt jest ładowany ( [CArchive:: IsLoading](#isloading) zwraca wartość różną od zera). Powinno to być pierwsze wywołanie `Serialize` funkcji i wywoływana tylko raz. Wartość zwracana przez (UINT)-1 oznacza, że numer wersji jest nieznany.

`CObject`Klasa pochodna może używać VERSIONABLE_SCHEMA połączonej (przy użyciu bitowej **lub**) z samą wersją schematu (w makrze IMPLEMENT_SERIAL), aby utworzyć "obiekt z obsługą wersji", czyli obiekt, którego `Serialize` funkcja członkowska może odczytywać wiele wersji. Domyślna funkcjonalność platformy (bez VERSIONABLE_SCHEMA) to zgłoszenie wyjątku, gdy wersja jest niezgodna.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#15](../../mfc/codesnippet/cpp/carchive-class_4.cpp)]

## <a name="carchiveisbufferempty"></a><a name="isbufferempty"></a>CArchive:: IsBufferEmpty

Wywołaj tę funkcję elementu członkowskiego, aby określić, czy wewnętrzny bufor obiektu archiwum jest pusty.

```
BOOL IsBufferEmpty() const;
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli bufor archiwum jest pusty; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja jest dostarczana do obsługi programowania przy użyciu klasy Windows Sockets MFC `CSocketFile` . Nie trzeba używać jej do archiwizacji skojarzonej z `CFile` obiektem.

Przyczyną użycia `IsBufferEmpty` z archiwum skojarzoną z `CSocketFile` obiektem jest fakt, że bufor archiwum może zawierać więcej niż jeden komunikat lub rekord. Po otrzymaniu jednego komunikatu należy użyć `IsBufferEmpty` programu, aby kontrolować pętlę, która kontynuuje pobieranie danych do momentu, gdy bufor jest pusty. Aby uzyskać więcej informacji, zobacz Funkcja [odbierania](../../mfc/reference/casyncsocket-class.md#receive) elementu członkowskiego klasy `CAsyncSocket` , która pokazuje, jak używać `IsBufferEmpty` .

Aby uzyskać więcej informacji, zobacz [Windows Sockets: używanie gniazd z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="carchiveisloading"></a><a name="isloading"></a>CArchive:: IsLoading

Określa, czy archiwum ładuje dane.

```
BOOL IsLoading() const;
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli archiwum jest aktualnie używane do ładowania; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana przez `Serialize` funkcje archiwizowanych klas.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#16](../../mfc/codesnippet/cpp/carchive-class_5.cpp)]

## <a name="carchiveisstoring"></a><a name="isstoring"></a>CArchive:: isprzechowywanie

Określa, czy archiwum przechowuje dane.

```
BOOL IsStoring() const;
```

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli archiwum jest aktualnie używane do przechowywania; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana przez `Serialize` funkcje archiwizowanych klas.

Jeśli `IsStoring` stan archiwum jest różny od zera, jego `IsLoading` stan to 0 i odwrotnie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#17](../../mfc/codesnippet/cpp/carchive-class_6.cpp)]

## <a name="carchivemapobject"></a><a name="mapobject"></a>CArchive:: MapObject

Wywołaj tę funkcję elementu członkowskiego, aby umieścić obiekty w mapie, które nie są naprawdę serializowane do pliku, ale które są dostępne dla podobiektów do odwołania.

```cpp
void MapObject(const CObject* pOb);
```

### <a name="parameters"></a>Parametry

*pOb*<br/>
Stały wskaźnik do przechowywanego obiektu.

### <a name="remarks"></a>Uwagi

Na przykład nie można serializować dokumentu, ale można serializować elementy, które są częścią dokumentu. Wywoływanie `MapObject` , zezwalasz na te elementy lub podobiekty, aby odwołać się do dokumentu. Ponadto serializowane elementy podelementowe mogą serializować swój *m_pDocument* wskaźnik wsteczny.

Możesz wywołać, `MapObject` gdy zapisujesz i ładujesz `CArchive` obiekt. `MapObject`Dodaje określony obiekt do wewnętrznych struktur danych obsługiwanych przez `CArchive` obiekt podczas serializacji i deserializacji, ale w przeciwieństwie do [ReadObject](#readobject) i [WriteObject](#writeobject)nie wywołuje serializacji obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#18](../../mfc/codesnippet/cpp/carchive-class_7.h)]

[!code-cpp[NVC_MFCSerialization#19](../../mfc/codesnippet/cpp/carchive-class_8.cpp)]

[!code-cpp[NVC_MFCSerialization#20](../../mfc/codesnippet/cpp/carchive-class_9.h)]

[!code-cpp[NVC_MFCSerialization#21](../../mfc/codesnippet/cpp/carchive-class_10.cpp)]

## <a name="carchivem_pdocument"></a><a name="m_pdocument"></a>CArchive:: m_pDocument

Domyślnie ustawiona na wartość NULL, ten wskaźnik do elementu `CDocument` można ustawić dla wszystkich elementów użytkownika `CArchive` wystąpienia.

```
CDocument* m_pDocument;
```

### <a name="remarks"></a>Uwagi

Typowym użyciem tego wskaźnika jest przekazywanie dodatkowych informacji o procesie serializacji do wszystkich obiektów, które są serializowane. Można to osiągnąć, inicjując wskaźnik przy użyciu dokumentu ( `CDocument` klasy pochodnej), który jest serializowany w taki sposób, że obiekty w dokumencie mają dostęp do dokumentu, w razie potrzeby. Ten wskaźnik jest również używany przez `COleClientItem` obiekty podczas serializacji.

Struktura ustawia *m_pDocument* do dokumentu, który jest serializowany, gdy użytkownik wystawia plik Otwórz lub Zapisz. W przypadku serializacji dokumentu kontenera łączącego i osadzania (OLE) z przyczyn innych niż otwieranie lub zapisywanie pliku należy jawnie ustawić *m_pDocument*. Na przykład, można to zrobić podczas serializacji dokumentu kontenera do Schowka.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#35](../../mfc/codesnippet/cpp/carchive-class_11.cpp)]

## <a name="carchiveoperator-ltlt"></a><a name="operator_lt_lt"></a>CArchive:: operator&lt;&lt;

Zapisuje wskazany obiekt lub typ pierwotny do archiwum.

```
friend CArchive& operator<<(
    CArchive& ar,
    const CObject* pOb);

throw(
    CArchiveException*,
    CFileException*);

CArchive& AFXAPI operator<<(
    CArchive& ar,
    const RECT& rect);

CArchive& AFXAPI operator<<(
    CArchive& ar,
    POINT point);

CArchive& AFXAPI operator<<(
    CArchive& ar,
    SIZE size);

template<typename BaseType,
    class StringTraits> CArchive& operator<<(
    const ATL::CStringT<BaseType,
    StringTraits>& str);

CArchive& operator<<(BYTE by);
CArchive& operator<<(WORD w);
CArchive& operator<<(LONG l);
CArchive& operator<<(DWORD dw);
CArchive& operator<<(float f);
CArchive& operator<<(double d);
CArchive& operator<<(int i);
CArchive& operator<<(short w);
CArchive& operator<<(char ch);
CArchive& operator<<(wchar_t ch);
CArchive& operator<<(unsigned u);
CArchive& operator<<(bool b);
CArchive& operator<<(ULONGLONG dwdw);
CArchive& operator<<(LONGLONG dwdw);
```

### <a name="return-value"></a>Wartość zwracana

`CArchive`Odwołanie, które umożliwia wielokrotne operatory wstawiania w pojedynczym wierszu.

### <a name="remarks"></a>Uwagi

Ostatnie dwie wersje zostały zaprojektowane z myślą o przechowywaniu 64-bitowych liczb całkowitych.

Jeśli użyto makra IMPLEMENT_SERIAL w implementacji klasy, operator wstawiania przeciążony dla `CObject` wywołań chronionych `WriteObject` . Ta funkcja z kolei wywołuje `Serialize` funkcję klasy.

Operator wstawiania [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) (<<) obsługuje zrzucanie diagnostyczne i przechowywanie w archiwum.

### <a name="example"></a>Przykład

Ten przykład ilustruje użycie `CArchive` operatora wstawiania << z **`int`** **`long`** typami i.

[!code-cpp[NVC_MFCSerialization#31](../../mfc/codesnippet/cpp/carchive-class_12.cpp)]

### <a name="example"></a>Przykład

Ten przykład 2 ilustruje użycie `CArchive` operatora wstawiania << z `CStringT` typem.

[!code-cpp[NVC_MFCSerialization#32](../../mfc/codesnippet/cpp/carchive-class_13.cpp)]

## <a name="carchiveoperator-gtgt"></a><a name="operator_gt_gt"></a>CArchive:: operator&gt;&gt;

Ładuje wskazany obiekt lub typ pierwotny z archiwum.

```
friend CArchive& operator>>(
    CArchive& ar,
    CObject *& pOb);

throw(
    CArchiveException*,
    CFileException*,
    CMemoryException*);

friend CArchive& operator>>(
    CArchive& ar,
    const CObject *& pOb);

throw(
    CArchiveException*,
    CFileException*,
    CMemoryException*);

CArchive& AFXAPI operator>>(
    CArchive& ar,
    const RECT& rect);

CArchive& AFXAPI operator>>(
    CArchive& ar,
    POINT point);

CArchive& AFXAPI operator>>(
    CArchive& ar,
    SIZE size);

template<typename BaseType,
    class StringTraits> CArchive& operator>>(
    ATL::CStringT<BaseType,
    StringTraits>& str);

CArchive& operator>>(BYTE& by);
CArchive& operator>>(WORD& w);
CArchive& operator>>(int& i);
CArchive& operator>>(LONG& l);
CArchive& operator>>(DWORD& dw);
CArchive& operator>>(float& f);
CArchive& operator>>(double& d);
CArchive& operator>>(short& w);
CArchive& operator>>(char& ch);
CArchive& operator>>(wchar_t& ch);
CArchive& operator>>(unsigned& u);
CArchive& operator>>(bool& b);
CArchive& operator>>(ULONGLONG& dwdw);
CArchive& operator>>(LONGLONG& dwdw);
```

### <a name="return-value"></a>Wartość zwracana

`CArchive`Odwołanie, które umożliwia wielokrotne operatory wyodrębniania w jednym wierszu.

### <a name="remarks"></a>Uwagi

Ostatnie dwie wersje zostały przeznaczone do ładowania 64-bitowych liczb całkowitych.

Jeśli w implementacji klasy użyto makra IMPLEMENT_SERIAL, to operatory wyodrębniania przeciążone dla `CObject` wywołania funkcji chronionej `ReadObject` (z niezerowym wskaźnikiem klasy czasu wykonywania). Ta funkcja z kolei wywołuje `Serialize` funkcję klasy.

Operator wyodrębniania [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) (>>) obsługuje ładowanie z archiwum.

### <a name="example"></a>Przykład

Ten przykład ilustruje użycie `CArchive` operatora ekstrakcji >> z **`int`** typem.

[!code-cpp[NVC_MFCSerialization#33](../../mfc/codesnippet/cpp/carchive-class_14.cpp)]

### <a name="example"></a>Przykład

W tym przykładzie pokazano użycie `CArchive` operatorów wstawiania i wyodrębniania <\< and >> z `CStringT` typem.

[!code-cpp[NVC_MFCSerialization#34](../../mfc/codesnippet/cpp/carchive-class_15.cpp)]

## <a name="carchiveread"></a><a name="read"></a>CArchive:: Read

Odczytuje określoną liczbę bajtów z archiwum.

```
UINT Read(void* lpBuf, UINT nMax);
```

### <a name="parameters"></a>Parametry

*lpBuf*<br/>
Wskaźnik do buforu dostarczonego przez użytkownika, który ma otrzymywać dane odczytane z archiwum.

*Nmaks.*<br/>
Liczba całkowita bez znaku określająca liczbę bajtów, które mają zostać odczytane z archiwum.

### <a name="return-value"></a>Wartość zwracana

Liczba całkowita bez znaku zawierająca liczbę bajtów, które są faktycznie odczytywane. Jeśli wartość zwracana jest mniejsza niż żądana liczba, osiągnięto koniec pliku. Nie zgłoszono wyjątku dla stanu końca pliku.

### <a name="remarks"></a>Uwagi

Archiwum nie interpretuje bajtów.

Można używać `Read` funkcji składowej w ramach `Serialize` funkcji do odczytywania zwykłych struktur, które są zawarte w obiektach.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#24](../../mfc/codesnippet/cpp/carchive-class_16.cpp)]

## <a name="carchivereadclass"></a><a name="readclass"></a>CArchive:: ReadClass

Wywołaj tę funkcję elementu członkowskiego, aby odczytać odwołanie do klasy, która została wcześniej zapisana z [WriteClass](#writeclass).

```
CRuntimeClass* ReadClass(
    const CRuntimeClass* pClassRefRequested = NULL,
    UINT* pSchema = NULL,
    DWORD* pObTag = NULL);
```

### <a name="parameters"></a>Parametry

*pClassRefRequested*<br/>
Wskaźnik do struktury [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , który odnosi się do żądanego odwołania do klasy. Może mieć wartość NULL.

*pSchema*<br/>
Wskaźnik do schematu klasy czasu wykonywania wcześniej przechowywanej.

*pObTag*<br/>
Liczba, która odnosi się do unikatowego tagu obiektu. Używane wewnętrznie przez implementację obiektu [ReadObject](#readobject). Dostępne tylko dla zaawansowanego programowania; *pObTag* zwykle powinna mieć wartość null.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do struktury [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) .

### <a name="remarks"></a>Uwagi

Jeśli *pClassRefRequested* nie ma wartości null, `ReadClass` sprawdza, czy zarchiwizowane informacje o klasie są zgodne z klasą środowiska uruchomieniowego. Jeśli nie jest zgodny, `ReadClass` program zgłosi [CArchiveException](../../mfc/reference/carchiveexception-class.md).

Klasa środowiska uruchomieniowego musi używać [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) i [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); w przeciwnym razie program `ReadClass` zgłosi [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Jeśli *pSchema* ma wartość null, schemat przechowywanej klasy można pobrać, wywołując [CArchive:: GetObjectSchema](#getobjectschema); w przeciwnym razie <strong>\*</strong> *pSchema* będzie zawierać schemat klasy czasu wykonywania, która była wcześniej przechowywana.

Można użyć [SerializeClass](#serializeclass) zamiast `ReadClass` , który obsługuje odczytywanie i zapisywanie odwołania do klasy.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CArchive:: WriteClass](#writeclass).

## <a name="carchivereadobject"></a><a name="readobject"></a>CArchive:: ReadObject

Odczytuje dane obiektu z archiwum i konstruuje obiekt odpowiedniego typu.

```
CObject* ReadObject(const CRuntimeClass* pClass);
```

### <a name="parameters"></a>Parametry

*pClass*<br/>
Stały wskaźnik do struktury [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , który odnosi się do obiektu, który powinien zostać odczytany.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik [CObject](../../mfc/reference/cobject-class.md) , który musi być bezpiecznie rzutowany do właściwej klasy pochodnej przy użyciu [CObject:: IsKindOf](../../mfc/reference/cobject-class.md#iskindof).

### <a name="remarks"></a>Uwagi

Ta funkcja jest zwykle wywoływana przez `CArchive` operator wyodrębniania ( **>>** ) przeciążony dla wskaźnika [CObject](../../mfc/reference/cobject-class.md) . `ReadObject`z kolei program wywołuje `Serialize` funkcję klasy archiwalnej.

W przypadku podania niezerowego parametru *pClass* , który jest uzyskiwany przez makro [RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class) , funkcja weryfikuje klasę czasu wykonywania zarchiwizowanego obiektu. Przyjęto założenie, że w implementacji klasy użyto makra IMPLEMENT_SERIAL.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CArchive:: WriteObject](#writeobject).

## <a name="carchivereadstring"></a><a name="readstring"></a>CArchive:: ReadString

Wywołaj tę funkcję elementu członkowskiego, aby odczytać dane tekstowe do buforu z pliku skojarzonego z `CArchive` obiektem.

```
BOOL ReadString(CString& rString);
LPTSTR ReadString(LPTSTR lpsz, UINT nMax);
```

### <a name="parameters"></a>Parametry

*rString*<br/>
Odwołanie do elementu [CString](../../atl-mfc-shared/reference/cstringt-class.md) , który będzie zawierać wynikowy ciąg po odczytaniu z pliku skojarzonego z obiektem CArchive.

*lpsz*<br/>
Określa wskaźnik do buforu dostarczonego przez użytkownika, który będzie otrzymywał ciąg tekstowy zakończony wartością null.

*Nmaks.*<br/>
Określa maksymalną liczbę znaków do odczytania. Wartość musi być mniejsza niż rozmiar buforu *lpsz* .

### <a name="return-value"></a>Wartość zwracana

W wersji, która zwraca wartość logiczną, prawda, jeśli pomyślne; W przeciwnym razie zwraca wartość FALSE.

W wersji, która zwraca `LPTSTR` , wskaźnik do buforu zawierającego dane tekstowe; Wartość NULL, jeśli osiągnięto koniec pliku.

### <a name="remarks"></a>Uwagi

W wersji funkcji składowej z parametrem *nmaks.* długość buforu będzie ograniczona do *nmaks.* -1 znaków. Odczyt został zatrzymany przez parę wysuwu wiersza powrotu karetki. Końcowe znaki nowego wiersza są zawsze usuwane. W obu przypadkach dołączany jest znak null (' \ 0 ').

[CArchive:: Read](#read) jest również dostępna dla danych wejściowych w trybie tekstowym, ale nie kończy się na parze wysuwu wiersza powrotu karetki.

### <a name="example"></a>Przykład

  Zobacz przykład dla [CArchive:: WriteString](#writestring).

## <a name="carchiveserializeclass"></a><a name="serializeclass"></a>CArchive:: SerializeClass

Wywołaj tę funkcję elementu członkowskiego, jeśli chcesz przechowywać i ładować informacje o wersji klasy bazowej.

```cpp
void SerializeClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>Parametry

*pClassRef*<br/>
Wskaźnik do obiektu klasy czasu wykonywania dla klasy bazowej.

### <a name="remarks"></a>Uwagi

`SerializeClass`odczytuje lub zapisuje odwołanie do klasy do `CArchive` obiektu, w zależności od kierunku `CArchive` . Użyj zamiast `SerializeClass` [ReadClass](#readclass) i [WriteClass](#writeclass) jako wygodnego sposobu serializacji obiektów klasy podstawowej; `SerializeClass` wymaga mniej kodu i mniejszej liczby parametrów.

`ReadClass`Na przykład `SerializeClass` sprawdza, czy zarchiwizowane informacje o klasie są zgodne z klasą środowiska uruchomieniowego. Jeśli nie jest zgodny, `SerializeClass` program zgłosi [CArchiveException](../../mfc/reference/carchiveexception-class.md).

Klasa środowiska uruchomieniowego musi używać [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) i [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); w przeciwnym razie program `SerializeClass` zgłosi [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Użyj makra [RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class) , aby pobrać wartość parametru *pRuntimeClass* . Klasa bazowa musi używać makra [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#25](../../mfc/codesnippet/cpp/carchive-class_17.h)]

## <a name="carchivesetloadparams"></a><a name="setloadparams"></a>CArchive:: SetLoadParams

Wywołaj `SetLoadParams` , gdy zamierzasz odczytać dużą liczbę `CObject` obiektów pochodnych z archiwum.

```cpp
void SetLoadParams(UINT nGrowBy = 1024);
```

### <a name="parameters"></a>Parametry

*nGrowBy*<br/>
Minimalna liczba gniazd elementów do przydzielenia w przypadku konieczności zwiększenia rozmiaru.

### <a name="remarks"></a>Uwagi

`CArchive`używa tablicy obciążenia do rozpoznawania odwołań do obiektów przechowywanych w archiwum. `SetLoadParams`umożliwia ustawienie rozmiaru, do którego zostanie powiększona tablica obciążenia.

Nie należy wywoływać `SetLoadParams` po załadowaniu jakiegokolwiek obiektu lub po wywołaniu metody [MapObject](#mapobject) lub [ReadObject](#readobject) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

## <a name="carchivesetobjectschema"></a><a name="setobjectschema"></a>CArchive:: SetObjectSchema

Wywołaj tę funkcję elementu członkowskiego, aby ustawić schemat obiektu przechowywany w obiekcie archiwum do *nSchema*.

```cpp
void SetObjectSchema(UINT nSchema);
```

### <a name="parameters"></a>Parametry

*nSchema*<br/>
Określa schemat obiektu.

### <a name="remarks"></a>Uwagi

Następne wywołanie [GetObjectSchema](#getobjectschema) zwróci wartość przechowywaną w *nSchema*.

Służy `SetObjectSchema` do zaawansowanej wersji, na przykład w przypadku, gdy chcesz wymusić odczytanie określonej wersji w `Serialize` funkcji klasy pochodnej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#27](../../mfc/codesnippet/cpp/carchive-class_19.cpp)]

## <a name="carchivesetstoreparams"></a><a name="setstoreparams"></a>CArchive:: SetStoreParams

Używany `SetStoreParams` podczas przechowywania dużej liczby `CObject` obiektów pochodnych w archiwum.

```cpp
void SetStoreParams(UINT nHashSize = 2053, UINT nBlockSize = 128);
```

### <a name="parameters"></a>Parametry

*nHashSize*<br/>
Rozmiar tabeli skrótów dla map wskaźnika interfejsu. Powinna to być liczba podstawowa.

*nBlockSize*<br/>
Określa stopień szczegółowości alokacji pamięci na potrzeby rozszerzania parametrów. W celu uzyskania najlepszej wydajności powinna być potęgą 2.

### <a name="remarks"></a>Uwagi

`SetStoreParams`umożliwia ustawienie rozmiaru tabeli skrótu i rozmiaru bloku mapy używanego do identyfikowania unikatowych obiektów podczas procesu serializacji.

Nie należy wywoływać `SetStoreParams` po zapisaniu obiektów lub po wywołaniu metody [MapObject](#mapobject) lub [WriteObject](#writeobject) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

## <a name="carchivewrite"></a><a name="write"></a>CArchive:: Write

Zapisuje określoną liczbę bajtów do archiwum.

```cpp
void Write(const void* lpBuf, INT nMax);
```

### <a name="parameters"></a>Parametry

*lpBuf*<br/>
Wskaźnik do buforu dostarczonego przez użytkownika, który zawiera dane, które mają być zapisywane w archiwum.

*Nmaks.*<br/>
Liczba całkowita określająca liczbę bajtów, które mają być zapisywane w archiwum.

### <a name="remarks"></a>Uwagi

Archiwum nie formatuje bajtów.

Możesz użyć `Write` funkcji elementu członkowskiego w `Serialize` funkcji, aby napisać zwykłe struktury, które są zawarte w obiektach.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#23](../../mfc/codesnippet/cpp/carchive-class_20.cpp)]

## <a name="carchivewriteclass"></a><a name="writeclass"></a>CArchive:: WriteClass

Służy `WriteClass` do przechowywania informacji o wersji i klasie klasy bazowej podczas serializacji klasy pochodnej.

```cpp
void WriteClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>Parametry

*pClassRef*<br/>
Wskaźnik do struktury [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , który odnosi się do żądanego odwołania do klasy.

### <a name="remarks"></a>Uwagi

`WriteClass`zapisuje odwołanie do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) dla klasy bazowej do `CArchive` . Użyj [CArchive:: ReadClass](#readclass) , aby pobrać odwołanie.

`WriteClass`sprawdza, czy zarchiwizowane informacje o klasie są zgodne z klasą środowiska uruchomieniowego. Jeśli nie jest zgodny, `WriteClass` program zgłosi [CArchiveException](../../mfc/reference/carchiveexception-class.md).

Klasa środowiska uruchomieniowego musi używać [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) i [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); w przeciwnym razie program `WriteClass` zgłosi [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Można użyć [SerializeClass](#serializeclass) zamiast `WriteClass` , który obsługuje odczytywanie i zapisywanie odwołania do klasy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#28](../../mfc/codesnippet/cpp/carchive-class_21.cpp)]

## <a name="carchivewriteobject"></a><a name="writeobject"></a>CArchive:: WriteObject

Przechowuje określony `CObject` do archiwum.

```cpp
void WriteObject(const CObject* pOb);
```

### <a name="parameters"></a>Parametry

*pOb*<br/>
Stały wskaźnik do przechowywanego obiektu.

### <a name="remarks"></a>Uwagi

Ta funkcja jest zwykle wywoływana przez `CArchive` operator wstawiania ( **<<** ) przeciążony dla `CObject` . `WriteObject`z kolei program wywołuje `Serialize` funkcję klasy archiwalnej.

Aby włączyć archiwizowanie, należy użyć makra IMPLEMENT_SERIAL. `WriteObject`zapisuje nazwę klasy ASCII w archiwum. Ta nazwa klasy jest weryfikowana w dalszej części procesu ładowania. Specjalny schemat kodowania zapobiega niepotrzebnemu duplikowaniu nazwy klasy dla wielu obiektów klasy. Ten schemat uniemożliwia również nadmiarowy magazyn obiektów, które są obiektami docelowymi więcej niż jeden wskaźnik.

Dokładne metody kodowania obiektów (łącznie z obecnością nazwy klasy ASCII) są szczegółami implementacji i mogą ulec zmianie w przyszłych wersjach biblioteki.

> [!NOTE]
> Zakończ tworzenie, usuwanie i aktualizowanie wszystkich obiektów przed rozpoczęciem ich archiwizowania. Archiwum zostanie uszkodzone w przypadku mieszania archiwizacji z modyfikacją obiektu.

### <a name="example"></a>Przykład

Aby zapoznać się z definicją klasy `CAge` , zobacz przykład dla [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist).

[!code-cpp[NVC_MFCSerialization#29](../../mfc/codesnippet/cpp/carchive-class_22.cpp)]

## <a name="carchivewritestring"></a><a name="writestring"></a>CArchive:: WriteString

Użyj tej funkcji elementu członkowskiego, aby zapisać dane z buforu do pliku skojarzonego z `CArchive` obiektem.

```cpp
void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>Parametry

*lpsz*<br/>
Określa wskaźnik do buforu zawierającego ciąg tekstowy zakończony znakiem null.

### <a name="remarks"></a>Uwagi

Kończący znak null (' \ 0 ') nie jest zapisywana w pliku; nie jest automatycznie pisany nowy wiersz.

`WriteString`zgłasza wyjątek w odpowiedzi na kilka warunków, w tym dysk — pełen warunek.

`Write`jest również dostępna, ale zamiast kończąc na znaku null, zapisuje żądaną liczbę bajtów do pliku.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#30](../../mfc/codesnippet/cpp/carchive-class_23.cpp)]

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CFile](../../mfc/reference/cfile-class.md)<br/>
[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Klasa CSocket](../../mfc/reference/csocket-class.md)<br/>
[Klasa CSocketFile](../../mfc/reference/csocketfile-class.md)
