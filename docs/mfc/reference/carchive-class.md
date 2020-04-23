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
ms.openlocfilehash: ef8b6ec9060e8c15dd45f8203dadd2a2aca9e168
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753118"
---
# <a name="carchive-class"></a>Klasa CArchive

Umożliwia zapisanie złożonej sieci obiektów w stałej formie binarnej (zwykle magazynu dysku), która utrzymuje się po usunięciu tych obiektów.

## <a name="syntax"></a>Składnia

```
class CArchive
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CArchive::CArchive](#carchive)|Tworzy obiekt `CArchive`.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CArchive::Abort](#abort)|Zamyka archiwum bez zgłaszania wyjątku.|
|[CArchive::Zamknij](#close)|Opróżnia niepisane dane i `CFile`rozłącza się z .|
|[CArchive::Flush](#flush)|Opróżnia niepisane dane z buforu archiwum.|
|[CArchive::GetFile](#getfile)|Pobiera `CFile` wskaźnik obiektu dla tego archiwum.|
|[CArchive::GetObjectSchema](#getobjectschema)|Wywoływana `Serialize` z funkcji, aby określić wersję obiektu, który jest deserializacji.|
|[CArchive::IsBufferEmpty](#isbufferempty)|Określa, czy bufor został opróżniony podczas procesu odbierania gniazd systemu Windows.|
|[CArchive::IsLoading](#isloading)|Określa, czy archiwum jest ładowane.|
|[CArchive::IsStoring](#isstoring)|Określa, czy archiwum jest przechowywane.|
|[CArchive::MapObject](#mapobject)|Umieszcza obiekty na mapie, które nie są serializowane do pliku, ale które są dostępne dla podobiektów do odwołania.|
|[CArchive::Czytaj](#read)|Odczytuje nieprzetworzone bajty.|
|[CArchive::ReadClass](#readclass)|Odczytuje odwołanie do klasy `WriteClass`wcześniej przechowywane z .|
|[CArchive::ReadObject](#readobject)|Wywołuje `Serialize` funkcję obiektu do ładowania.|
|[CArchive::ReadString](#readstring)|Odczytuje pojedynczy wiersz tekstu.|
|[CArchive::SerializeClass](#serializeclass)|Odczytuje lub zapisuje odwołanie `CArchive` do klasy do `CArchive`obiektu w zależności od kierunku .|
|[CArchive::SetLoadParams](#setloadparams)|Ustawia rozmiar, do którego zwiększa się tablica obciążenia. Musi być wywoływana, zanim `MapObject` dowolny `ReadObject` obiekt jest ładowany lub przed lub jest wywoływana.|
|[CArchive::SetObjectSchema](#setobjectschema)|Ustawia schemat obiektu przechowywany w obiekcie archiwum.|
|[CArchive::SetStoreParams](#setstoreparams)|Ustawia rozmiar tabeli mieszania i rozmiar bloku mapy używanej do identyfikowania unikatowych obiektów podczas procesu serializacji.|
|[CArchive::Zapis](#write)|Zapisuje nieprzetworzone bajty.|
|[CArchive::WriteClass](#writeclass)|Zapisuje odwołanie `CRuntimeClass` do . `CArchive`|
|[CArchive::WriteObject](#writeobject)|Wywołuje `Serialize` funkcję obiektu do przechowywania.|
|[CArchive::WriteString](#writestring)|Zapisuje pojedynczy wiersz tekstu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CArchive::operator&lt;&lt;](#operator_lt_lt)|Przechowuje obiekty i typy pierwotne w archiwum.|
|[CArchive::operator&gt;&gt;](#operator_gt_gt)|Ładuje obiekty i typy pierwotne z archiwum.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CArchive::m_pDocument](#m_pdocument)||

## <a name="remarks"></a>Uwagi

`CArchive`nie ma klasy podstawowej.

Później można załadować obiekty z magazynu trwałego, odtwarzając je w pamięci. Ten proces tworzenia danych trwałe jest nazywany "serializacji."

Obiekt archiwum można potraktować jako rodzaj strumienia binarnego. Podobnie jak strumień wejścia/wyjścia, archiwum jest skojarzone z plikiem i umożliwia buforowane zapisywanie i odczytywanie danych do i z magazynu. Strumień wejściowy/wyjściowy przetwarza sekwencje znaków ASCII, ale archiwum przetwarza dane obiektów binarnych w wydajnym, niedoścignionym formacie.

Przed utworzeniem `CArchive` obiektu należy utworzyć obiekt [CFile.](../../mfc/reference/cfile-class.md) Ponadto należy upewnić się, że stan ładowania/przechowywania archiwum jest zgodny z trybem otwierania pliku. Jesteś ograniczony do jednego aktywnego archiwum na plik.

Podczas konstruowania `CArchive` obiektu, należy dołączyć go `CFile` do obiektu klasy (lub klasy pochodnej), który reprezentuje otwarty plik. Należy również określić, czy archiwum będzie używane do ładowania lub przechowywania. Obiekt `CArchive` może przetwarzać nie tylko typy pierwotne, ale także obiekty klas pochodnych [CObject](../../mfc/reference/cobject-class.md)przeznaczonych do serializacji. Klasa serializable zwykle `Serialize` ma funkcję elementu członkowskiego i zwykle używa [makr DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) i [IMPLEMENT_SERIAL,](../../mfc/reference/run-time-object-model-services.md#implement_serial) `CObject`zgodnie z opisem w klasie .

Przeciążone ekstrakcji ( **>>**) **<<** i wstawiania ( ) operatory są `CObject`wygodne interfejsy programowania archiwum, które obsługują zarówno typy pierwotne i -pochodne klasy.

`CArchive`obsługuje również programowanie z MFC Windows Sockets klasy [CSocket](../../mfc/reference/csocket-class.md) i [CSocketFile](../../mfc/reference/csocketfile-class.md). Funkcja elementu członkowskiego [IsBufferEmpty](#isbufferempty) obsługuje to użycie.

Aby uzyskać `CArchive`więcej informacji na temat , zobacz artykuły [Serializacja](../../mfc/serialization-in-mfc.md) i [Gniazda systemu Windows: Korzystanie z gniazd z archiwum](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CArchive`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="carchiveabort"></a><a name="abort"></a>CArchive::Abort

Wywołanie tej funkcji, aby zamknąć archiwum bez zgłaszania wyjątku.

```cpp
void Abort ();
```

### <a name="remarks"></a>Uwagi

Destruktor `CArchive` zwykle wywoła `Close`, co spowoduje opróżnienie wszystkich danych, które `CFile` nie zostały zapisane w skojarzonym obiekcie. Może to powodować wyjątki.

Podczas przechwytywania tych wyjątków, jest `Abort`dobrym pomysłem, aby `CArchive` użyć , tak, że destrukcja obiektu nie powoduje dalszych wyjątków. Podczas obsługi wyjątków, `CArchive::Abort` nie zgłasza wyjątek na błędy, ponieważ, w przeciwieństwie do [CArchive::Close](#close), `Abort` ignoruje błędy.

Jeśli użyto **nowego** `CArchive` do przydzielenia obiektu na stosie, należy go usunąć po zamknięciu pliku.

### <a name="example"></a>Przykład

  Zobacz przykład [CArchive::WriteClass](#writeclass).

## <a name="carchivecarchive"></a><a name="carchive"></a>CArchive::CArchive

Konstruuje `CArchive` obiekt i określa, czy będzie on używany do ładowania lub przechowywania obiektów.

```
CArchive(
    CFile* pFile,
    UINT nMode,
    int nBufSize = 4096,
    void* lpBuf = NULL);
```

### <a name="parameters"></a>Parametry

*p Plik*<br/>
Wskaźnik do `CFile` obiektu, który jest ostatecznym źródłem lub miejscem docelowym danych trwałych.

*nMode*<br/>
Flaga określająca, czy obiekty będą ładowane z archiwum, czy przechowywane do archiwum. Parametr *nMode* musi mieć jedną z następujących wartości:

- `CArchive::load`Ładuje dane z archiwum. Wymaga `CFile` tylko uprawnienia do odczytu.

- `CArchive::store`Zapisuje dane w archiwum. Wymaga `CFile` uprawnień do zapisu.

- `CArchive::bNoFlushOnDelete`Zapobiega automatycznemu wywoływaniu `Flush` archiwum po wywołaniu destruktora archiwum. Jeśli ustawisz tę flagę, jesteś `Close` odpowiedzialny za jawne wywołanie przed destruktor jest wywoływany. Jeśli tego nie zrobisz, Twoje dane zostaną uszkodzone.

*nBufSize (Rozmiar)*<br/>
Liczba całkowita określająca rozmiar wewnętrznego buforu plików w bajtach. Należy zauważyć, że domyślny rozmiar buforu wynosi 4096 bajtów. Jeśli rutynowo archiwizujesz duże obiekty, zwiększysz wydajność, jeśli użyjesz większego rozmiaru buforu, który jest wielokrotnością rozmiaru buforu plików.

*lpBuf (właśc.*<br/>
Opcjonalny wskaźnik do dostarczonego przez użytkownika bufora o rozmiarze *nBufSize*. Jeśli ten parametr nie zostanie określony, archiwum przydziela bufor ze sterty lokalnej i zwalnia go po zniszczeniu obiektu. Archiwum nie zwalnia buforu dostarczonego przez użytkownika.

### <a name="remarks"></a>Uwagi

Po utworzeniu archiwum nie można zmienić tej specyfikacji.

Nie można `CFile` używać operacji do zmiany stanu pliku, dopóki nie zostanie zamknięte archiwum. Każda taka operacja spowoduje uszkodzenie integralności archiwum. Można uzyskać dostęp do pozycji wskaźnika pliku w dowolnym momencie podczas serializacji, uzyskując obiekt pliku archiwum z funkcji elementu członkowskiego [GetFile,](#getfile) a następnie za pomocą funkcji [CFile::GetPosition.](../../mfc/reference/cfile-class.md#getposition) Należy wywołać [CArchive::Flush](#flush) przed uzyskaniem pozycji wskaźnika pliku.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#12](../../mfc/codesnippet/cpp/carchive-class_1.cpp)]

## <a name="carchiveclose"></a><a name="close"></a>CArchive::Zamknij

Opróżnia wszystkie dane pozostające w buforze, zamyka archiwum i odłącza archiwum od pliku.

```cpp
void Close();
```

### <a name="remarks"></a>Uwagi

Dalsze operacje w archiwum nie są dozwolone. Po zamknięciu archiwum można utworzyć inne archiwum dla tego samego pliku lub zamknąć plik.

Funkcja `Close` elementu członkowskiego zapewnia, że wszystkie dane są przesyłane z archiwum do pliku i sprawia, że archiwum jest niedostępne. Aby zakończyć transfer z pliku na nośnik pamięci, należy najpierw użyć [CFile::Close,](../../mfc/reference/cfile-class.md#close) a następnie zniszczyć `CFile` obiekt.

### <a name="example"></a>Przykład

  Zobacz przykład [CArchive::WriteString](#writestring).

## <a name="carchiveflush"></a><a name="flush"></a>CArchive::Flush

Wymusza zapisanie w pliku wszystkich danych pozostających w buforze archiwum.

```cpp
void Flush();
```

### <a name="remarks"></a>Uwagi

Funkcja `Flush` elementu członkowskiego zapewnia, że wszystkie dane są przesyłane z archiwum do pliku. Aby zakończyć transfer z pliku na nośnik magazynu, należy wywołać [plik CFile::Close.](../../mfc/reference/cfile-class.md#close)

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#13](../../mfc/codesnippet/cpp/carchive-class_2.cpp)]

## <a name="carchivegetfile"></a><a name="getfile"></a>CArchive::GetFile

Pobiera `CFile` wskaźnik obiektu dla tego archiwum.

```
CFile* GetFile() const;
```

### <a name="return-value"></a>Wartość zwracana

Stały wskaźnik do `CFile` używanego obiektu.

### <a name="remarks"></a>Uwagi

Przed użyciem `GetFile`pliku .

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#14](../../mfc/codesnippet/cpp/carchive-class_3.cpp)]

## <a name="carchivegetobjectschema"></a><a name="getobjectschema"></a>CArchive::GetObjectSchema

Wywołanie tej `Serialize` funkcji z funkcji, aby określić wersję obiektu, który jest obecnie deserializacji.

```
UINT GetObjectSchema();
```

### <a name="return-value"></a>Wartość zwracana

Podczas deserializacji, wersja obiektu jest odczytywany.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji jest `CArchive` prawidłowe tylko wtedy, gdy obiekt jest ładowany ( [CArchive::IsLoading](#isloading) zwraca nonzero). Powinno to być pierwsze `Serialize` wywołanie w funkcji i wywoływane tylko raz. Zwracana wartość (UINT)-1 wskazuje, że numer wersji jest nieznany.

Klasa `CObject`pochodna może używać VERSIONABLE_SCHEMA łączona (przy użyciu bitowego **OR)** z samą wersją schematu (w IMPLEMENT_SERIAL makra) do `Serialize` utworzenia "obiekcie zdatnym do versionable", czyli obiektu, którego funkcja elementu członkowskiego może odczytywać wiele wersji. Domyślna funkcjonalność struktury (bez VERSIONABLE_SCHEMA) jest zgłosić wyjątek, gdy wersja jest niezgodna.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#15](../../mfc/codesnippet/cpp/carchive-class_4.cpp)]

## <a name="carchiveisbufferempty"></a><a name="isbufferempty"></a>CArchive::IsBufferEmpty

Wywołanie tej funkcji elementu członkowskiego, aby ustalić, czy bufor wewnętrzny obiektu archiwum jest pusty.

```
BOOL IsBufferEmpty() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli bufor archiwum jest pusty; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja jest dostarczana do obsługi programowania `CSocketFile`z MFC Windows Sockets klasy . Nie trzeba go używać do archiwum skojarzonego z obiektem. `CFile`

Powodem użycia `IsBufferEmpty` z archiwum skojarzonym z obiektem `CSocketFile` jest to, że bufor archiwum może zawierać więcej niż jedną wiadomość lub rekord. Po otrzymaniu jednej wiadomości, `IsBufferEmpty` należy użyć do kontrolowania pętli, która kontynuuje odbieranie danych, aż bufor jest pusty. Aby uzyskać więcej [Receive](../../mfc/reference/casyncsocket-class.md#receive) informacji, zobacz `CAsyncSocket`Receive funkcji elementu `IsBufferEmpty`członkowskiego klasy , który pokazuje, jak używać .

Aby uzyskać więcej informacji, zobacz [Gniazda systemu Windows: Korzystanie z gniazd z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="carchiveisloading"></a><a name="isloading"></a>CArchive::IsLoading

Określa, czy archiwum ładuje dane.

```
BOOL IsLoading() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli archiwum jest obecnie używany do ładowania; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego `Serialize` jest wywoływana przez funkcje zarchiwizowanych klas.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#16](../../mfc/codesnippet/cpp/carchive-class_5.cpp)]

## <a name="carchiveisstoring"></a><a name="isstoring"></a>CArchive::IsStoring

Określa, czy archiwum przechowuje dane.

```
BOOL IsStoring() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli archiwum jest obecnie używany do przechowywania; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego `Serialize` jest wywoływana przez funkcje zarchiwizowanych klas.

Jeśli `IsStoring` stan archiwum jest niezerowy, `IsLoading` jego stan wynosi 0 i odwrotnie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#17](../../mfc/codesnippet/cpp/carchive-class_6.cpp)]

## <a name="carchivemapobject"></a><a name="mapobject"></a>CArchive::MapObject

Wywołanie tej funkcji elementu członkowskiego, aby umieścić obiekty na mapie, które nie są tak naprawdę serializowane do pliku, ale które są dostępne dla podobiektów do odwołania.

```cpp
void MapObject(const CObject* pOb);
```

### <a name="parameters"></a>Parametry

*Pob*<br/>
Stały wskaźnik do przechowywanego obiektu.

### <a name="remarks"></a>Uwagi

Na przykład nie można serializować dokumentu, ale należy serializować elementy, które są częścią dokumentu. Wywołując `MapObject`program , umożliwia odwoływanie się do dokumentu przez te elementy lub podobiekty. Ponadto serializowane podpozycje mogą serializować ich *m_pDocument* wskaźnika wstecz.

Wywołanie `MapObject` można podczas przechowywania i `CArchive` ładowania z obiektu. `MapObject`dodaje określony obiekt do wewnętrznych struktur danych `CArchive` obsługiwanych przez obiekt podczas serializacji i deserializacji, ale w przeciwieństwie do [ReadObject](#readobject) i [WriteObject](#writeobject), nie wymaga serializacji na obiekcie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#18](../../mfc/codesnippet/cpp/carchive-class_7.h)]

[!code-cpp[NVC_MFCSerialization#19](../../mfc/codesnippet/cpp/carchive-class_8.cpp)]

[!code-cpp[NVC_MFCSerialization#20](../../mfc/codesnippet/cpp/carchive-class_9.h)]

[!code-cpp[NVC_MFCSerialization#21](../../mfc/codesnippet/cpp/carchive-class_10.cpp)]

## <a name="carchivem_pdocument"></a><a name="m_pdocument"></a>CArchive::m_pDocument

Domyślnie ustawiona na wartość `CDocument` NULL, ten wskaźnik do `CArchive` a można ustawić na wszystko, co użytkownik wystąpienia chce.

```
CDocument* m_pDocument;
```

### <a name="remarks"></a>Uwagi

Typowym zastosowaniem tego wskaźnika jest przekazanie dodatkowych informacji o procesie serializacji do wszystkich obiektów serializowanych. Osiąga się to poprzez zainicjowanie wskaźnika `CDocument`z dokumentem (klasa pochodna), który jest serializowany, w taki sposób, że obiekty w dokumencie mogą uzyskać dostęp do dokumentu, jeśli to konieczne. Ten wskaźnik jest `COleClientItem` również używany przez obiekty podczas serializacji.

Struktura ustawia *m_pDocument* do dokumentu serializowanego, gdy użytkownik wystawia polecenie Otwieranie pliku lub Zapisz. W przypadku serializacji dokumentu kontenera łączenia i osadzania obiektów (OLE) z powodów innych niż Otwieranie plików lub Zapisywanie należy jawnie ustawić *m_pDocument*. Na przykład można to zrobić podczas serializacji dokumentu kontenera do Schowka.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#35](../../mfc/codesnippet/cpp/carchive-class_11.cpp)]

## <a name="carchiveoperator-ltlt"></a><a name="operator_lt_lt"></a>CArchive::operator&lt;&lt;

Przechowuje wskazany obiekt lub typ pierwotny w archiwum.

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

Odwołanie, `CArchive` które umożliwia wiele operatorów wstawiania w jednym wierszu.

### <a name="remarks"></a>Uwagi

Dwie ostatnie wersje powyżej są specjalnie do przechowywania 64-bitowych liczby całkowite.

Jeśli użyto makra IMPLEMENT_SERIAL w implementacji klasy, operator wstawiania przeciążony dla `CObject` wywołuje chroniony `WriteObject`. . Ta funkcja z kolei `Serialize` wywołuje funkcję klasy.

Operator wstawiania [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) (<<) obsługuje diagnostykę dumpingu i przechowywania w archiwum.

### <a name="example"></a>Przykład

W tym przykładzie pokazano `CArchive` użycie operatora wstawiania << z typami **int** i **long.**

[!code-cpp[NVC_MFCSerialization#31](../../mfc/codesnippet/cpp/carchive-class_12.cpp)]

### <a name="example"></a>Przykład

W tym przykładzie 2 `CArchive` przedstawiono użycie operatora wstawiania << z typem. `CStringT`

[!code-cpp[NVC_MFCSerialization#32](../../mfc/codesnippet/cpp/carchive-class_13.cpp)]

## <a name="carchiveoperator-gtgt"></a><a name="operator_gt_gt"></a>CArchive::operator&gt;&gt;

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

Odwołanie, `CArchive` które umożliwia wiele operatorów ekstrakcji w jednym wierszu.

### <a name="remarks"></a>Uwagi

Ostatnie dwie wersje powyżej są specjalnie do ładowania 64-bitowych liczbach całkowitych.

Jeśli użyto makra IMPLEMENT_SERIAL w implementacji klasy, operatory wyodrębniania przeciążone dla `CObject` wywołania `ReadObject` funkcji chronionej (z wskaźnikiem klasy wykonywania niezerowego). Ta funkcja z kolei `Serialize` wywołuje funkcję klasy.

Operator wyodrębniania [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) (>>) obsługuje ładowanie z archiwum.

### <a name="example"></a>Przykład

W tym przykładzie pokazano `CArchive` użycie operatora ekstrakcji >> z **typem int.**

[!code-cpp[NVC_MFCSerialization#33](../../mfc/codesnippet/cpp/carchive-class_14.cpp)]

### <a name="example"></a>Przykład

W tym przykładzie pokazano `CArchive` użycie operatorów wstawiania i ekstrakcji <\< i >> z typem. `CStringT`

[!code-cpp[NVC_MFCSerialization#34](../../mfc/codesnippet/cpp/carchive-class_15.cpp)]

## <a name="carchiveread"></a><a name="read"></a>CArchive::Czytaj

Odczytuje określoną liczbę bajtów z archiwum.

```
UINT Read(void* lpBuf, UINT nMax);
```

### <a name="parameters"></a>Parametry

*lpBuf (właśc.*<br/>
Wskaźnik do buforu dostarczonego przez użytkownika, który ma odbierać dane odczytane z archiwum.

*Nmax*<br/>
Niepodpisana liczba całkowita określająca liczbę bajtów do odczytu z archiwum.

### <a name="return-value"></a>Wartość zwracana

Niepodpisana liczba całkowita zawierająca liczbę bajtów faktycznie odczytywanych. Jeśli wartość zwracana jest mniejsza niż żądana liczba, osiągnięto koniec pliku. Nie wyjątek jest zgłaszany na koniec pliku warunek.

### <a name="remarks"></a>Uwagi

Archiwum nie interpretuje bajtów.

Funkcji `Read` elementu członkowskiego w `Serialize` ramach funkcji można używać do odczytywania zwykłych struktur, które są zawarte w obiektach.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#24](../../mfc/codesnippet/cpp/carchive-class_16.cpp)]

## <a name="carchivereadclass"></a><a name="readclass"></a>CArchive::ReadClass

Wywołanie tej funkcji elementu członkowskiego, aby odczytać odwołanie do klasy wcześniej przechowywane z [WriteClass](#writeclass).

```
CRuntimeClass* ReadClass(
    const CRuntimeClass* pClassRefRequested = NULL,
    UINT* pSchema = NULL,
    DWORD* pObTag = NULL);
```

### <a name="parameters"></a>Parametry

*pClassRefRequested (Odmowa śr.*<br/>
Wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) struktury, która odpowiada odwołanie do żądanej klasy. Może mieć wartość NULL.

*pSchema ( pSchema )*<br/>
Wskaźnik do schematu klasy wykonywania czasu wcześniej przechowywane.

*pObTag*<br/>
Liczba, która odwołuje się do unikatowego tagu obiektu. Używany wewnętrznie przez implementację [ReadObject](#readobject). Widoczne tylko dla zaawansowanego programowania; *pObTag* normalnie powinien mieć wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) struktury.

### <a name="remarks"></a>Uwagi

Jeśli *pClassRefRequested* nie `ReadClass` jest null, sprawdza, czy informacje o klasie zarchiwizowanej jest zgodna z klasy środowiska wykonawczego. Jeśli nie jest `ReadClass` kompatybilny, rzuci [CArchiveException](../../mfc/reference/carchiveexception-class.md).

Klasa środowiska wykonawczego musi używać [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) i [IMPLEMENT_SERIAL;](../../mfc/reference/run-time-object-model-services.md#implement_serial) w `ReadClass` przeciwnym razie wrzuci [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Jeśli *pSchema* ma wartość NULL, schemat przechowywanej klasy można pobrać, wywołując [CArchive::GetObjectSchema](#getobjectschema); w <strong>\*</strong>przeciwnym razie *pSchema* będzie zawierać schemat klasy run-time, który był wcześniej przechowywany.

Zamiast `ReadClass`programu SerializeClass można użyć [serializeclass,](#serializeclass) która obsługuje zarówno odczyt, jak i zapis odwołania do klasy.

### <a name="example"></a>Przykład

  Zobacz przykład [CArchive::WriteClass](#writeclass).

## <a name="carchivereadobject"></a><a name="readobject"></a>CArchive::ReadObject

Odczytuje dane obiektu z archiwum i konstruuje obiekt odpowiedniego typu.

```
CObject* ReadObject(const CRuntimeClass* pClass);
```

### <a name="parameters"></a>Parametry

*pClass (klasa pClass)*<br/>
Stały wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) struktury, która odpowiada obiekt, który oczekuje się odczytać.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik [CObject,](../../mfc/reference/cobject-class.md) który musi być bezpiecznie rzutowany do poprawnej klasy pochodnej przy użyciu [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof).

### <a name="remarks"></a>Uwagi

Ta funkcja jest zwykle `CArchive` wywoływana **>>** przez operator ekstrakcji ( ) przeciążony dla wskaźnika [CObject.](../../mfc/reference/cobject-class.md) `ReadObject`, z kolei `Serialize` wywołuje funkcję zarchiwizowanej klasy.

Jeśli podasz niezerowy parametr *pClass,* który jest uzyskiwany przez [makro RUNTIME_CLASS,](../../mfc/reference/run-time-object-model-services.md#runtime_class) funkcja weryfikuje klasę czasu wykonywania zarchiwizowanego obiektu. Zakłada się, że użyto makra IMPLEMENT_SERIAL w implementacji klasy.

### <a name="example"></a>Przykład

  Zobacz przykład [CArchive::WriteObject](#writeobject).

## <a name="carchivereadstring"></a><a name="readstring"></a>CArchive::ReadString

Wywołanie tej funkcji elementu członkowskiego, aby odczytać dane `CArchive` tekstowe do buforu z pliku skojarzonego z obiektem.

```
BOOL ReadString(CString& rString);
LPTSTR ReadString(LPTSTR lpsz, UINT nMax);
```

### <a name="parameters"></a>Parametry

*rString*<br/>
Odwołanie do [CString,](../../atl-mfc-shared/reference/cstringt-class.md) który będzie zawierał wynikowy ciąg po jego odczytaniu z pliku skojarzonego z CArchive obiektu.

*lpsz (lpsz)*<br/>
Określa wskaźnik do buforu dostarczonego przez użytkownika, który otrzyma ciąg tekstowy zakończony z wartością null.

*Nmax*<br/>
Określa maksymalną liczbę znaków do odczytu. Powinien być o jeden mniejszy niż rozmiar bufora *lpsz.*

### <a name="return-value"></a>Wartość zwracana

W wersji zwraca bool, prawda, jeśli zakończy się pomyślnie; FAŁSZ inaczej.

W wersji, która `LPTSTR`zwraca , wskaźnik do buforu zawierającego dane tekstowe; NULL, jeśli osiągnięto koniec pliku.

### <a name="remarks"></a>Uwagi

W wersji funkcji elementu członkowskiego z parametrem *nMax* bufor będzie trzymał do limitu *nMax* - 1 znaków. Odczyt jest zatrzymywany przez parę wiersza powrotu karetki. Końcowe znaki nowej linii są zawsze usuwane. Znak zerowy ('\0') jest dołączany w obu przypadkach.

[CArchive::Read](#read) jest również dostępny dla danych wejściowych w trybie tekstowym, ale nie kończy się na parze kanału informacyjnego wiersza powrotu karetki.

### <a name="example"></a>Przykład

  Zobacz przykład [CArchive::WriteString](#writestring).

## <a name="carchiveserializeclass"></a><a name="serializeclass"></a>CArchive::SerializeClass

Wywołanie tej funkcji elementu członkowskiego, gdy chcesz przechowywać i ładować informacje o wersji klasy podstawowej.

```cpp
void SerializeClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>Parametry

*pClassRef (Odnośnik)*<br/>
Wskaźnik do obiektu klasy run-time dla klasy podstawowej.

### <a name="remarks"></a>Uwagi

`SerializeClass`odczytuje lub zapisuje odwołanie do `CArchive` klasy do obiektu, `CArchive`w zależności od kierunku . Użyj `SerializeClass` zamiast [ReadClass](#readclass) i [WriteClass](#writeclass) jako wygodny sposób serializacji obiektów klasy podstawowej; `SerializeClass` wymaga mniej kodu i mniej parametrów.

Like `ReadClass` `SerializeClass` , sprawdza, czy informacje o klasie zarchiwizowanej jest zgodny z klasy runtime. Jeśli nie jest `SerializeClass` kompatybilny, rzuci [CArchiveException](../../mfc/reference/carchiveexception-class.md).

Klasa środowiska wykonawczego musi używać [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) i [IMPLEMENT_SERIAL;](../../mfc/reference/run-time-object-model-services.md#implement_serial) w `SerializeClass` przeciwnym razie wrzuci [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Użyj [makra RUNTIME_CLASS,](../../mfc/reference/run-time-object-model-services.md#runtime_class) aby pobrać wartość parametru *pRuntimeClass.* Klasa podstawowa musi używać [makra IMPLEMENT_SERIAL.](../../mfc/reference/run-time-object-model-services.md#implement_serial)

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#25](../../mfc/codesnippet/cpp/carchive-class_17.h)]

## <a name="carchivesetloadparams"></a><a name="setloadparams"></a>CArchive::SetLoadParams

Wywołaj, `SetLoadParams` gdy zamierzasz odczytać `CObject`dużą liczbę obiektów pochodnych z archiwum.

```cpp
void SetLoadParams(UINT nGrowBy = 1024);
```

### <a name="parameters"></a>Parametry

*nGrowBy ( nGrowBy )*<br/>
Minimalna liczba slotów elementu do przydzielenia, jeśli konieczne jest zwiększenie rozmiaru.

### <a name="remarks"></a>Uwagi

`CArchive`używa tablicy obciążenia, aby rozpoznać odwołania do obiektów przechowywanych w archiwum. `SetLoadParams`umożliwia ustawienie rozmiaru, do którego rośnie tablica obciążenia.

Nie wolno `SetLoadParams` wywoływać po załadowaniu dowolnego obiektu lub po [wywołaniu MapObject](#mapobject) lub [ReadObject.](#readobject)

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

## <a name="carchivesetobjectschema"></a><a name="setobjectschema"></a>CArchive::SetObjectSchema

Wywołanie tej funkcji elementu członkowskiego, aby ustawić schemat obiektu przechowywanego w obiekcie archiwum na *nSchema*.

```cpp
void SetObjectSchema(UINT nSchema);
```

### <a name="parameters"></a>Parametry

*nSchema ( nSchema )*<br/>
Określa schemat obiektu.

### <a name="remarks"></a>Uwagi

Następne wywołanie [GetObjectSchema](#getobjectschema) zwróci wartość przechowywaną w *nSchema*.

Służy `SetObjectSchema` do zaawansowanego przechowywania wersji; na przykład, gdy chcesz wymusić określoną wersję `Serialize` do odczytu w funkcji klasy pochodnej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#27](../../mfc/codesnippet/cpp/carchive-class_19.cpp)]

## <a name="carchivesetstoreparams"></a><a name="setstoreparams"></a>CArchive::SetStoreParams

Służy `SetStoreParams` do przechowywania dużej `CObject`liczby obiektów pochodnych w archiwum.

```cpp
void SetStoreParams(UINT nHashSize = 2053, UINT nBlockSize = 128);
```

### <a name="parameters"></a>Parametry

*nHashSize (Rozmiar)*<br/>
Rozmiar tabeli mieszania dla map wskaźnika interfejsu. Powinien być liczbą pierwszą.

*nBlockSize (Rozmiar)*<br/>
Określa szczegółowość alokacji pamięci w celu rozszerzenia parametrów. Powinien być moc 2 dla najlepszej wydajności.

### <a name="remarks"></a>Uwagi

`SetStoreParams`umożliwia ustawienie rozmiaru tabeli mieszania i rozmiaru bloku mapy używanej do identyfikowania unikatowych obiektów podczas procesu serializacji.

Nie można `SetStoreParams` wywołać po żadnych obiektów są przechowywane lub po [MapObject](#mapobject) lub [WriteObject](#writeobject) jest wywoływana.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

## <a name="carchivewrite"></a><a name="write"></a>CArchive::Zapis

Zapisuje określoną liczbę bajtów do archiwum.

```cpp
void Write(const void* lpBuf, INT nMax);
```

### <a name="parameters"></a>Parametry

*lpBuf (właśc.*<br/>
Wskaźnik do buforu dostarczonego przez użytkownika, który zawiera dane, które mają być zapisywane w archiwum.

*Nmax*<br/>
Liczba całkowita określająca liczbę bajtów, które mają zostać zapisane w archiwum.

### <a name="remarks"></a>Uwagi

Archiwum nie formatuje bajtów.

Funkcji `Write` elementu członkowskiego w `Serialize` ramach funkcji można zapisywać zwykłe struktury, które są zawarte w obiektach.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#23](../../mfc/codesnippet/cpp/carchive-class_20.cpp)]

## <a name="carchivewriteclass"></a><a name="writeclass"></a>CArchive::WriteClass

Służy `WriteClass` do przechowywania informacji o wersji i klasie klasy podstawowej podczas serializacji klasy pochodnej.

```cpp
void WriteClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>Parametry

*pClassRef (Odnośnik)*<br/>
Wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) struktury, która odpowiada odwołanie do żądanej klasy.

### <a name="remarks"></a>Uwagi

`WriteClass`zapisuje odwołanie do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) dla klasy `CArchive`podstawowej do . Użyj [CArchive::ReadClass,](#readclass) aby pobrać odwołanie.

`WriteClass`sprawdza, czy informacje o klasie zarchiwizowanej są zgodne z klasą środowiska wykonawczego. Jeśli nie jest `WriteClass` kompatybilny, rzuci [CArchiveException](../../mfc/reference/carchiveexception-class.md).

Klasa środowiska wykonawczego musi używać [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) i [IMPLEMENT_SERIAL;](../../mfc/reference/run-time-object-model-services.md#implement_serial) w `WriteClass` przeciwnym razie wrzuci [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Zamiast `WriteClass`programu SerializeClass można użyć [serializeclass,](#serializeclass) która obsługuje zarówno odczyt, jak i zapis odwołania do klasy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#28](../../mfc/codesnippet/cpp/carchive-class_21.cpp)]

## <a name="carchivewriteobject"></a><a name="writeobject"></a>CArchive::WriteObject

Przechowuje `CObject` określone w archiwum.

```cpp
void WriteObject(const CObject* pOb);
```

### <a name="parameters"></a>Parametry

*Pob*<br/>
Stały wskaźnik do przechowywanego obiektu.

### <a name="remarks"></a>Uwagi

Ta funkcja jest zwykle `CArchive` wywoływana **<<** przez operator wstawiania ( ) przeciążony dla `CObject`. `WriteObject`, z kolei `Serialize` wywołuje funkcję zarchiwizowanej klasy.

Aby umożliwić archiwizację, należy użyć makra IMPLEMENT_SERIAL. `WriteObject`zapisuje nazwę klasy ASCII do archiwum. Ta nazwa klasy jest sprawdzana później podczas procesu ładowania. Specjalny schemat kodowania zapobiega niepotrzebnemu powielaniu nazwy klasy dla wielu obiektów klasy. Ten schemat zapobiega również nadmiarowego przechowywania obiektów, które są obiektami docelowymi więcej niż jednego wskaźnika.

Metoda dokładnego kodowania obiektów (w tym obecność nazwy klasy ASCII) jest szczegółem implementacji i może ulec zmianie w przyszłych wersjach biblioteki.

> [!NOTE]
> Zakończ tworzenie, usuwanie i aktualizowanie wszystkich obiektów przed rozpoczęciem ich archiwizowania. Archiwum zostanie uszkodzone, jeśli zmieszasz archiwizację z modyfikacją obiektu.

### <a name="example"></a>Przykład

Definicja klasy `CAge`można znaleźć w przykładzie [CObList::CObList](../../mfc/reference/coblist-class.md#coblist).

[!code-cpp[NVC_MFCSerialization#29](../../mfc/codesnippet/cpp/carchive-class_22.cpp)]

## <a name="carchivewritestring"></a><a name="writestring"></a>CArchive::WriteString

Ta funkcja elementu członkowskiego służy do zapisywania danych `CArchive` z bufora do pliku skojarzonego z obiektem.

```cpp
void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>Parametry

*lpsz (lpsz)*<br/>
Określa wskaźnik do buforu zawierającego ciąg tekstowy zakończony wartością null.

### <a name="remarks"></a>Uwagi

Kończący się znak null ('\0') nie jest zapisywany w pliku; nie jest automatycznie zapisywany nowy.

`WriteString`zgłasza wyjątek w odpowiedzi na kilka warunków, w tym warunek pełnego dysku.

`Write`jest również dostępna, ale zamiast kończyć na znaku zerowym, zapisuje żądaną liczbę bajtów do pliku.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#30](../../mfc/codesnippet/cpp/carchive-class_23.cpp)]

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CFile](../../mfc/reference/cfile-class.md)<br/>
[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Klasa CSocket](../../mfc/reference/csocket-class.md)<br/>
[Klasa CSocketFile](../../mfc/reference/csocketfile-class.md)
