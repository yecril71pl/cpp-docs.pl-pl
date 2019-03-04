---
title: CArchive — klasa
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
ms.openlocfilehash: 8f169964c6a313f37b5ea50a5105af29af7b59b1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266331"
---
# <a name="carchive-class"></a>CArchive — klasa

Umożliwia zapisanie złożonej sieci obiektów w stałą postać binarną (zazwyczaj pamięć dyskowa), która utrzymuje się po usunięciu tych obiektów.

## <a name="syntax"></a>Składnia

```
class CArchive
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CArchive::CArchive](#carchive)|Tworzy `CArchive` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CArchive::Abort](#abort)|Zamyka archiwum bez zgłoszenia wyjątku.|
|[CArchive::Close](#close)|Opróżnia niezapisanych danych i zamknie połączenie z tym `CFile`.|
|[CArchive::Flush](#flush)|Opróżnia niezapisanych danych z bufora archiwum.|
|[CArchive::GetFile](#getfile)|Pobiera `CFile` wskaźnik do obiektu tym archiwum.|
|[CArchive::GetObjectSchema](#getobjectschema)|Wywoływane z `Serialize` funkcję, aby określić wersję deserializowany jest obiekt.|
|[CArchive::IsBufferEmpty](#isbufferempty)|Określa, czy podczas Windows Sockets został opróżniony buforu odbierania procesu.|
|[CArchive::IsLoading](#isloading)|Określa, czy archiwum jest ładowany.|
|[CArchive::IsStoring](#isstoring)|Określa, czy jest przechowywanie archiwum.|
|[CArchive::MapObject](#mapobject)|Umieszcza mapy, które nie są serializowane w pliku, ale dostępnych do podobiektów, aby odwołać się do obiektów.|
|[CArchive::Read](#read)|Odczytuje bajtów raw.|
|[CArchive::ReadClass](#readclass)|Odczyty odwołań do klas uprzednio przechowywane w usłudze `WriteClass`.|
|[CArchive::ReadObject](#readobject)|Wywołuje obiekt `Serialize` funkcji do załadowania.|
|[CArchive::ReadString](#readstring)|Odczytuje pojedynczy wiersz tekstu.|
|[CArchive::SerializeClass](#serializeclass)|Operacja odczytu lub zapisu odwołań do klas do `CArchive` obiekt, w zależności od kierunku `CArchive`.|
|[CArchive::SetLoadParams](#setloadparams)|Określa rozmiar, do którego tablicy obciążenie rośnie. Musi zostać wywołana przed załadowaniem dowolnego obiektu lub przed `MapObject` lub `ReadObject` jest wywoływana.|
|[CArchive::SetObjectSchema](#setobjectschema)|Ustawia schematu obiektów przechowywanych w obiekcie archiwum.|
|[CArchive::SetStoreParams](#setstoreparams)|Ustawia rozmiar tabeli wyznaczania wartości skrótu i rozmiar bloku mapy, używany do identyfikowania następującą liczbę unikatowych obiektów podczas procesu serializacji.|
|[CArchive::Write](#write)|Zapisuje nieprzetworzone bajty.|
|[CArchive::WriteClass](#writeclass)|Zapisuje odwołanie do `CRuntimeClass` do `CArchive`.|
|[CArchive::WriteObject](#writeobject)|Wywołuje obiekt `Serialize` funkcji przechowywania.|
|[CArchive::WriteString](#writestring)|Zapisuje pojedynczy wiersz tekstu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CArchive::operator &lt;&lt;](#operator_lt_lt)|Przechowuje obiekty i typy pierwotne do archiwum.|
|[CArchive::operator &gt;&gt;](#operator_gt_gt)|Ładuje obiekty i typy pierwotne z archiwum.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CArchive::m_pDocument](#m_pdocument)||

## <a name="remarks"></a>Uwagi

`CArchive` nie ma klasy bazowej.

Później możesz załadować obiektów z magazynu trwałego przywracanie ich w pamięci. Udostępnianie trwałych danych ten proces jest nazywany "serializacji."

Można potraktować obiektu archiwum jako rodzaju strumienia danych binarnych. Np. strumień we/wy archiwum jest skojarzony z plikiem i zezwala na buforowanego zapisywania i odczytywania danych do i z magazynu. Strumień we/wy przetwarza sekwencje znaków ASCII, ale archiwum przetwarza dane binarne obiektu w formie wydajne, nonredundant.

Należy utworzyć [CFile](../../mfc/reference/cfile-class.md) obiektu, aby można było utworzyć `CArchive` obiektu. Ponadto upewnij się, że stan obciążenia/magazynowania archiwum jest zgodna z tryb otwarcia pliku. Są ograniczone do jednego aktywnego archiwum na plik.

Podczas konstruowania `CArchive` obiektu i dołączyć go do obiektu klasy `CFile` (lub klasę pochodną) reprezentujący otwartego pliku. Należy również określić, czy archiwum będą używane dla ładowania lub zapisywania. A `CArchive` obiektu może przetwarzać nie tylko typy pierwotne, ale także obiekty [CObject](../../mfc/reference/cobject-class.md)— przeznaczony dla serializacji klas pochodnych. Zwykle ma klasę serializacji `Serialize` funkcja elementu członkowskiego który zazwyczaj używa [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) i [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) makra, zgodnie z opisem w ramach klasy `CObject`.

Przeciążona wyodrębniania ( **>>**) i wstawiania ( **<<**) operatory to wygodne archiwum interfejsów, które obsługują oba typy pierwotne i `CObject` -klas pochodnych.

`CArchive` obsługuje również programowania przy użyciu klas MFC Windows Sockets [CSocket](../../mfc/reference/csocket-class.md) i [CSocketFile](../../mfc/reference/csocketfile-class.md). [IsBufferEmpty](#isbufferempty) funkcja elementu członkowskiego obsługuje to użycie.

Aby uzyskać więcej informacji na temat `CArchive`, zobacz artykuły [serializacji](../../mfc/serialization-in-mfc.md) i [Windows Sockets: Używanie gniazd z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CArchive`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="abort"></a>  CArchive::Abort

Wywołaj tę funkcję, aby zamknąć archiwum nie zostanie zgłoszony wyjątek.

```
void Abort ();
```

### <a name="remarks"></a>Uwagi

`CArchive` Zwykle wywoła destruktor `Close`, która spowoduje to opróżnienie wszystkich danych, które nie zostały zapisane do powiązanych `CFile` obiektu. Może to spowodować, że wyjątki.

Przechwytywanie tych wyjątków, jest dobry pomysł, aby użyć `Abort`, dzięki czemu destructing `CArchive` obiektu nie powoduje dalsze wyjątki. Podczas obsługi wyjątków, `CArchive::Abort` nie spowoduje zgłoszenie wyjątku na awarie ponieważ, w przeciwieństwie do [CArchive::Close](#close), `Abort` ignoruje błędy.

Jeśli użyto **nowe** przydzielić `CArchive` obiektów na stosie, należy je usunąć po zamknięciu pliku.

### <a name="example"></a>Przykład

  Zobacz przykład [CArchive::WriteClass](#writeclass).

##  <a name="carchive"></a>  CArchive::CArchive

Konstruuje `CArchive` obiektu i określa, czy będzie używana dla ładowania lub zapisywania obiektów.

```
CArchive(
    CFile* pFile,
    UINT nMode,
    int nBufSize = 4096,
    void* lpBuf = NULL);
```

### <a name="parameters"></a>Parametry

*pFile*<br/>
Wskaźnik do `CFile` obiekt, który jest źródło lub miejsce docelowe danych trwałych.

*nMode*<br/>
Flaga określająca, czy obiekty zostaną załadowane z lub przechowywane do archiwum. *NMode* parametr musi mieć jedną z następujących wartości:

- `CArchive::load` Ładuje dane z archiwum. Wymaga jedynie `CFile` uprawnienie do odczytu.

- `CArchive::store` Zapisuje dane do archiwum. Wymaga `CFile` uprawnienie do zapisu.

- `CArchive::bNoFlushOnDelete` Uniemożliwia automatyczne wywołanie archiwum `Flush` po destruktor archiwum jest wywoływany. Jeśli ta flaga jest ustawiona, odpowiedzialność za jawne wywołanie `Close` przed destruktor jest wywoływany. Jeśli tego nie zrobisz, Twoje dane będą uszkodzone.

*nBufSize*<br/>
Liczba całkowita określająca rozmiar buforu wewnętrznego pliku w bajtach. Należy pamiętać, że domyślny rozmiar buforu 4096 bajtów. Jeśli regularnie archiwizowany dużych obiektów, umożliwi zwiększenie wydajności, jeśli używasz większy rozmiar buforu, będąca wielokrotnością rozmiaru buforu pliku.

*lpBuf*<br/>
Opcjonalny operator wskaźnika do buforu dostarczone przez użytkownika o rozmiarze *nBufSize*. Jeśli ten parametr nie jest określony, archiwum przydziela bufor z lokalnej sterty i zwalnia je, kiedy niszczony jest obiekt. Archiwum nie spowoduje zwolnienia bufor dostarczone przez użytkownika.

### <a name="remarks"></a>Uwagi

Po utworzeniu archiwum, nie można zmienić tej specyfikacji.

Nie można używać `CFile` operacje, aby zmienić stan pliku, dopóki nie zostały zamknięte archiwum. Takie działanie spowoduje uszkodzić integralności archiwum. Użytkownik może uzyskać dostęp pozycja wskaźnika pliku w dowolnym momencie podczas serializacji, uzyskując obiektu pliku archiwum z [Pobieranie_pliku](#getfile) funkcja elementu członkowskiego, a następnie używając [CFile::GetPosition](../../mfc/reference/cfile-class.md#getposition) — funkcja . Należy wywołać [CArchive::Flush](#flush) przed uzyskaniem pozycja wskaźnika pliku.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#12](../../mfc/codesnippet/cpp/carchive-class_1.cpp)]

##  <a name="close"></a>  CArchive::Close

Czyści wszystkie dane pozostały w buforze, zamyka archiwum i odłącza archiwum z pliku.

```
void Close();
```

### <a name="remarks"></a>Uwagi

Nie dalszych operacji na archiwum są dozwolone. Po zamknięciu archiwum, można utworzyć archiwum innego dla tego samego pliku, lub można zamknąć pliku.

Funkcja elementu członkowskiego `Close` gwarantuje, że wszystkie dane są przesyłane z archiwum do pliku i jego powoduje, że archiwum. Aby ukończyć przeniesienie z pliku do nośnika magazynowania, należy najpierw użyć [CFile::Close](../../mfc/reference/cfile-class.md#close) a następnie zniszcz `CFile` obiektu.

### <a name="example"></a>Przykład

  Zobacz przykład [CArchive::WriteString](#writestring).

##  <a name="flush"></a>  CArchive::Flush

Wymusza wszelkie dane pozostały w buforze archiwum są zapisywane w pliku.

```
void Flush();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego `Flush` gwarantuje, że wszystkie dane są przesyłane z archiwum do pliku. Należy wywołać [CFile::Close](../../mfc/reference/cfile-class.md#close) można zakończyć transferu z pliku do nośnika magazynowania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#13](../../mfc/codesnippet/cpp/carchive-class_2.cpp)]

##  <a name="getfile"></a>  CArchive::GetFile

Pobiera `CFile` wskaźnik do obiektu tym archiwum.

```
CFile* GetFile() const;
```

### <a name="return-value"></a>Wartość zwracana

Stały wskaźnik do `CFile` obiektu w użyciu.

### <a name="remarks"></a>Uwagi

Należy opróżniania archiwum, przed rozpoczęciem korzystania z `GetFile`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#14](../../mfc/codesnippet/cpp/carchive-class_3.cpp)]

##  <a name="getobjectschema"></a>  CArchive::GetObjectSchema

Wywołaj tę funkcję z `Serialize` funkcję, aby określić wersję obiektu, który jest aktualnie przeprowadzona.

```
UINT GetObjectSchema();
```

### <a name="return-value"></a>Wartość zwracana

Podczas deserializacji, wersja obiektu odczytywany.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji jest prawidłowa tylko kiedy `CArchive` obiektów jest ładowany ( [CArchive::IsLoading](#isloading) zwraca wartość różną od zera). Powinno być to pierwsze wywołanie w `Serialize` funkcji i wywołana tylko raz. Zwracana wartość wynosząca (UINT) -1 wskazuje, że numer wersji jest nieznany.

A `CObject`-klasy pochodnej może używać w połączeniu VERSIONABLE_SCHEMA (przy użyciu bitowego **lub**) w wersji schematu (w IMPLEMENT_SERIAL — makro) do utworzenia "znalezienie obiekt", oznacza to, że obiekt którego `Serialize` Funkcja elementu członkowskiego może odczytywać wielu wersji. Domyślna funkcjonalność framework (bez VERSIONABLE_SCHEMA) jest zgłoszenie wyjątku, gdy wersja jest niezgodna.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#15](../../mfc/codesnippet/cpp/carchive-class_4.cpp)]

##  <a name="isbufferempty"></a>  CArchive::IsBufferEmpty

Wywołaj tę funkcję elementu członkowskiego, aby ustalić, czy bufor wewnętrzny obiekt archiwum jest pusty.

```
BOOL IsBufferEmpty() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli bufor archiwum jest pusta. w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja jest dostarczany do obsługi programowania przy użyciu klas MFC Windows Sockets `CSocketFile`. Nie należy używać go do archiwum skojarzone z `CFile` obiektu.

Przyczyna przy użyciu `IsBufferEmpty` z archiwum skojarzony `CSocketFile` obiekt jest, że bufor archiwum może zawierać więcej niż jednego komunikatu lub rekordu. Po otrzymaniu jeden komunikat, należy użyć `IsBufferEmpty` do kontrolowania pętli, który zwiększa odbierania danych, dopóki rozmiar buforu jest pusty. Aby uzyskać więcej informacji, zobacz [Receive](../../mfc/reference/casyncsocket-class.md#receive) funkcji składowej klasy typu `CAsyncSocket`, który ilustruje sposób używania `IsBufferEmpty`.

Aby uzyskać więcej informacji, zobacz [Windows Sockets: Używanie gniazd z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="isloading"></a>  CArchive::IsLoading

Określa, czy archiwum ładowania danych.

```
BOOL IsLoading() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli archiwum jest obecnie używana do ładowania; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana przez `Serialize` funkcje klas zarchiwizowane.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#16](../../mfc/codesnippet/cpp/carchive-class_5.cpp)]

##  <a name="isstoring"></a>  CArchive::IsStoring

Określa, czy archiwum jest przechowywanie danych.

```
BOOL IsStoring() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli archiwum jest aktualnie używany do przechowywania; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana przez `Serialize` funkcje klas zarchiwizowane.

Jeśli `IsStoring` stan archiwum jest różna od zera, a następnie jego `IsLoading` stan ma wartość 0 i na odwrót.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#17](../../mfc/codesnippet/cpp/carchive-class_6.cpp)]

##  <a name="mapobject"></a>  CArchive::MapObject

Wywołaj tę funkcję elementu członkowskiego, aby umieścić obiekty w mapie, którego tak naprawdę nie są serializowane w pliku, ale dostępnych do podobiektów do odwołania.

```
void MapObject(const CObject* pOb);
```

### <a name="parameters"></a>Parametry

*pOb*<br/>
Stały wskaźnik do obiektu są przechowywane.

### <a name="remarks"></a>Uwagi

Na przykład nie może serializować dokumentu, ale może serializować elementy, które są częścią dokumentu. Przez wywołanie metody `MapObject`, musisz zezwolić na te elementy lub podobiektów, aby odwoływać się do dokumentu. Ponadto podelementy Zserializowany może wykonywać serializację ich *m_pDocument* wskaźnik Wstecz.

Możesz wywołać `MapObject` podczas przechowywania, do i załadować z `CArchive` obiektu. `MapObject` Dodaje określony obiekt do struktur danych wewnętrznych utrzymywane przez `CArchive` obiektu podczas serializacji i deserializacji, ale w przeciwieństwie do [SE operace ReadObject](#readobject) i [SE operace WriteObject](#writeobject), nie wywołuje serializacji obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#18](../../mfc/codesnippet/cpp/carchive-class_7.h)]

[!code-cpp[NVC_MFCSerialization#19](../../mfc/codesnippet/cpp/carchive-class_8.cpp)]

[!code-cpp[NVC_MFCSerialization#20](../../mfc/codesnippet/cpp/carchive-class_9.h)]

[!code-cpp[NVC_MFCSerialization#21](../../mfc/codesnippet/cpp/carchive-class_10.cpp)]

##  <a name="m_pdocument"></a>  CArchive::m_pDocument

Domyślnie na wartość NULL, to wskaźnik do `CDocument` można ustawić żadnych użytkownik `CArchive` chce wystąpienia.

```
CDocument* m_pDocument;
```

### <a name="remarks"></a>Uwagi

Wspólne użycie tego wskaźnika jest przekazywanie dodatkowych informacji o procesie serializacji do wszystkich obiektów serializacji. Jest to osiągane przez inicjowanie wskaźnika z dokumentem ( `CDocument`-klasy pochodnej), które jest serializowana, w taki sposób, że obiektów w dokumencie można uzyskać dostęp do dokumentów, w razie potrzeby. This, wskaźnik jest również używany przez `COleClientItem` obiektów podczas serializacji.

Ustawia framework *m_pDocument* do dokumentu jest serializowana, gdy użytkownik generuje plik należy otworzyć lub zapisać polecenia. Jeśli serializujesz łączenie i osadzanie (OLE) dokumentu kontenera powodów innych niż Otwórz plik i Zapisz Musisz jawnie ustawić *m_pDocument*. Na przykład czy w tym podczas serializowania dokumentu kontenera do Schowka.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#35](../../mfc/codesnippet/cpp/carchive-class_11.cpp)]

##  <a name="operator_lt_lt"></a>  CArchive::operator &lt;&lt;

Przechowuje obiekt wskazany lub typ pierwotny do archiwum.

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

A `CArchive` odwołania, która umożliwia wielu operatorów wstawiania w jednym wierszu.

### <a name="remarks"></a>Uwagi

Ostatnie dwie wersje powyżej są przeznaczone na potrzeby przechowywania 64-bitowych liczb całkowitych.

Jeśli IMPLEMENT_SERIAL — makro jest używane w danej implementacji klasy, a następnie operator wstawiania przeciążona dla `CObject` wywołuje chronionej `WriteObject`. Z kolei wywołuje tę funkcję `Serialize` funkcji klasy.

[CStringT](../../atl-mfc-shared/reference/cstringt-class.md) operator wstawiania (<<) obsługuje diagnostycznych zrzucanie i przechowywania do archiwum.

### <a name="example"></a>Przykład

W tym przykładzie pokazano użycie `CArchive` operator wstawiania << z **int** i **długie** typów.

[!code-cpp[NVC_MFCSerialization#31](../../mfc/codesnippet/cpp/carchive-class_12.cpp)]

### <a name="example"></a>Przykład

W tym przykładzie 2 demonstruje użycie `CArchive` operator wstawiania << z `CStringT` typu.

[!code-cpp[NVC_MFCSerialization#32](../../mfc/codesnippet/cpp/carchive-class_13.cpp)]

##  <a name="operator_gt_gt"></a>  CArchive::operator &gt;&gt;

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

A `CArchive` odwołania, która umożliwia wielu operatorów wyodrębniania w jednym wierszu.

### <a name="remarks"></a>Uwagi

Ostatnie dwie wersje powyżej są przeznaczone na potrzeby ładowania 64-bitowych liczb całkowitych.

Jeśli IMPLEMENT_SERIAL — makro jest używane w danej implementacji klasy, a następnie operatorów wyodrębniania przeciążona dla `CObject` wywoływania chronionego `ReadObject` — funkcja (za pomocą wskaźnika wartość różną od zera klasie czasu wykonywania). Z kolei wywołuje tę funkcję `Serialize` funkcji klasy.

[CStringT](../../atl-mfc-shared/reference/cstringt-class.md) operatorów wyodrębniania (>>) obsługuje ładowanie z archiwum.

### <a name="example"></a>Przykład

W tym przykładzie pokazano użycie `CArchive` operator wyodrębniania >> z **int** typu.

[!code-cpp[NVC_MFCSerialization#33](../../mfc/codesnippet/cpp/carchive-class_14.cpp)]

### <a name="example"></a>Przykład

W tym przykładzie pokazano użycie `CArchive` operatory wstawienia i wydobycia <\< i >> z `CStringT` typu.

[!code-cpp[NVC_MFCSerialization#34](../../mfc/codesnippet/cpp/carchive-class_15.cpp)]

##  <a name="read"></a>  CArchive::Read

Odczytuje określoną liczbę bajtów z archiwum.

```
UINT Read(void* lpBuf, UINT nMax);
```

### <a name="parameters"></a>Parametry

*lpBuf*<br/>
Wskaźnik do buforu dostarczone przez użytkownika, który ma otrzymać dane odczytywane z archiwum.

*nMax*<br/>
Liczba całkowita bez znaku określający liczbę bajtów do odczytu z archiwum.

### <a name="return-value"></a>Wartość zwracana

Liczbą całkowitą bez znaku, zawierającą liczbę faktycznie odczytanych bajtów. Jeśli wartość zwracana jest mniejsza niż żądana, osiągnięto koniec pliku. Nie wyjątku, pod warunkiem końca pliku.

### <a name="remarks"></a>Uwagi

Archiwum nie interpretuje bajtów.

Możesz użyć `Read` funkcja elementu członkowskiego, w ramach Twojej `Serialize` funkcji dla zwykłych struktur, które są zawarte w obiekty do czytania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#24](../../mfc/codesnippet/cpp/carchive-class_16.cpp)]

##  <a name="readclass"></a>  CArchive::ReadClass

Wywołaj tę funkcję elementu członkowskiego, można odczytać odwołania do klasy uprzednio przechowywane w usłudze [WriteClass](#writeclass).

```
CRuntimeClass* ReadClass(
    const CRuntimeClass* pClassRefRequested = NULL,
    UINT* pSchema = NULL,
    DWORD* pObTag = NULL);
```

### <a name="parameters"></a>Parametry

*pClassRefRequested*<br/>
Wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) strukturę, która odnosi się do żądanego odwołania do klasy. Może mieć wartości NULL.

*pSchema*<br/>
Wskaźnik do schematu o klasie czasu wykonywania, wcześniej zapisane.

*pObTag*<br/>
Liczba, która odwołuje się do obiektu unikatowych tagów. Używane wewnętrznie przez implementację [SE operace ReadObject](#readobject). Narażone na zaawansowane umiejętności programistyczne. *pObTag* zwykle powinna być równa NULL.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) struktury.

### <a name="remarks"></a>Uwagi

Jeśli *pClassRefRequested* nie ma wartości NULL, `ReadClass` sprawdza, czy informacje zarchiwizowanego klasy jest zgodny z klasy środowiska uruchomieniowego. Jeśli nie jest zgodny, `ReadClass` zgłosi [CArchiveException](../../mfc/reference/carchiveexception-class.md).

Należy użyć klasy środowiska uruchomieniowego [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) i [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); w przeciwnym razie `ReadClass` zgłosi [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Jeśli *pSchema* ma wartość NULL, schematu przechowywanych klasy może być pobierany przez wywołanie [CArchive::GetObjectSchema](#getobjectschema); w przeciwnym razie <strong>\*</strong>  *pSchema* będzie zawierać schematu klasy środowiska wykonawczego, która została wcześniej zapisana.

Możesz użyć [SerializeClass](#serializeclass) zamiast `ReadClass`, która obsługuje Odczyt i zapis dla odwołania do klasy.

### <a name="example"></a>Przykład

  Zobacz przykład [CArchive::WriteClass](#writeclass).

##  <a name="readobject"></a>  CArchive::ReadObject

Odczytuje dane obiektu z archiwum i konstruuje obiekt odpowiedniego typu.

```
CObject* ReadObject(const CRuntimeClass* pClass);
```

### <a name="parameters"></a>Parametry

*pClass*<br/>
Stały wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) strukturę, która odpowiada obiektowi oczekiwany Odczyt.

### <a name="return-value"></a>Wartość zwracana

A [CObject](../../mfc/reference/cobject-class.md) wskaźnika, który musi być bezpiecznie rzutowany na prawidłowe klasy pochodnej za pomocą [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof).

### <a name="remarks"></a>Uwagi

Ta funkcja jest zazwyczaj wywoływana `CArchive` wyodrębniania ( **>>**) operator jest przeciążony dla [CObject](../../mfc/reference/cobject-class.md) wskaźnika. `ReadObject`, z kolei wywołuje `Serialize` funkcji klasy zarchiwizowane.

Jeśli podasz wartość różną od zera *pClass* parametr, który można uzyskać przez [RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class) — makro, a następnie funkcja sprawdza klasy środowiska wykonawczego zarchiwizowane obiektu. Przy założeniu, że używasz IMPLEMENT_SERIAL — makro w implementacji klasy.

### <a name="example"></a>Przykład

  Zobacz przykład [CArchive::WriteObject](#writeobject).

##  <a name="readstring"></a>  CArchive::ReadString

Wywołaj tę funkcję elementu członkowskiego do odczytywania danych tekstowych do buforu z pliku skojarzone z `CArchive` obiektu.

```
BOOL ReadString(CString& rString);
LPTSTR ReadString(LPTSTR lpsz, UINT nMax);
```

### <a name="parameters"></a>Parametry

*rString*<br/>
Odwołanie do [CString](../../atl-mfc-shared/reference/cstringt-class.md) po jest do odczytu z pliku skojarzone z obiektu CArchive będzie zawierające ciąg wynikowy.

*lpsz*<br/>
Określa wskaźnik do buforu dostarczone przez użytkownika, który będzie otrzymywał ciąg tekstowy zakończony znakiem null.

*nMax*<br/>
Określa maksymalną liczbę znaków do odczytania. Powinien być mniejszy niż rozmiar *lpsz* buforu.

### <a name="return-value"></a>Wartość zwracana

W wersji, która zwraca wartość TRUE, jeśli to się powiedzie; BOOL, Wartość FALSE w przeciwnym razie.

W wersji, która zwraca `LPTSTR`, wskaźnik do buforu zawierającą dane tekstowe; Wartość NULL, jeśli osiągnięto koniec pliku.

### <a name="remarks"></a>Uwagi

W wersji funkcji składowej z *nmaks* parametr, rozmiar buforu wstrzymuje do limitu *nmaks* - 1 znaków. Odczytywanie została zatrzymana przez parę wysuwu wiersza powrotu karetki. Końcowe znaki nowego wiersza, zawsze są usuwane. Znak null ('\0') jest dołączany w obu przypadkach.

[CArchive::Read](#read) jest również dostępna dla danych wejściowych w trybie tekstowym, ale nie kończy w parę wysuwu wiersza powrotu karetki.

### <a name="example"></a>Przykład

  Zobacz przykład [CArchive::WriteString](#writestring).

##  <a name="serializeclass"></a>  CArchive::SerializeClass

Wywołaj tę funkcję elementu członkowskiego, umożliwia przechowywanie i ładowanie informacji o klasie podstawowej wersji.

```
void SerializeClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>Parametry

*pClassRef*<br/>
Wskaźnik do obiektu klasy środowiska wykonawczego dla klasy podstawowej.

### <a name="remarks"></a>Uwagi

`SerializeClass` Operacja odczytu lub zapisu odwołania do klasy, aby `CArchive` obiektu, w zależności od kierunku `CArchive`. Użyj `SerializeClass` zamiast [ReadClass](#readclass) i [WriteClass](#writeclass) to wygodny sposób do wykonywania serializacji obiektów klasy bazowej; `SerializeClass` wymaga mniejszej ilości kodu i mniej parametrów.

Podobnie jak `ReadClass`, `SerializeClass` sprawdza, czy informacje zarchiwizowanego klasy jest zgodny z klasy środowiska uruchomieniowego. Jeśli nie jest zgodny, `SerializeClass` zgłosi [CArchiveException](../../mfc/reference/carchiveexception-class.md).

Należy użyć klasy środowiska uruchomieniowego [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) i [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); w przeciwnym razie `SerializeClass` zgłosi [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Użyj [RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class) makra, aby pobrać wartość *pRuntimeClass* parametru. Klasa bazowa ma zastosowanie tylko [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) makra.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#25](../../mfc/codesnippet/cpp/carchive-class_17.h)]

##  <a name="setloadparams"></a>  CArchive::SetLoadParams

Wywołaj `SetLoadParams` kiedy ma być odczyt dużej liczby `CObject`-obiektami wywodzącymi z archiwum.

```
void SetLoadParams(UINT nGrowBy = 1024);
```

### <a name="parameters"></a>Parametry

*nGrowBy*<br/>
Minimalna liczba gniazd element do przydzielenia, jeśli konieczne jest zwiększenie rozmiaru.

### <a name="remarks"></a>Uwagi

`CArchive` używa tablicy obciążenia do rozpoznawania odwołań do obiektów przechowywanych w archiwum. `SetLoadParams` Umożliwia ustawienie rozmiaru, do którego tablicy obciążenie rośnie.

Nie należy wywołać `SetLoadParams` po załadowaniu dowolnego obiektu lub po [MapObject](#mapobject) lub [SE operace ReadObject](#readobject) jest wywoływana.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

##  <a name="setobjectschema"></a>  CArchive::SetObjectSchema

Wywołaj tę funkcję elementu członkowskiego, aby ustawić schematu obiektów przechowywanych w obiekcie archiwum do *nSchema*.

```
void SetObjectSchema(UINT nSchema);
```

### <a name="parameters"></a>Parametry

*nSchema*<br/>
Określa schematu obiektu.

### <a name="remarks"></a>Uwagi

Następne wywołanie [GetObjectSchema](#getobjectschema) zwróci wartość przechowywaną w *nSchema*.

Użyj `SetObjectSchema` zaawansowanej wersji; na przykład, gdy chcesz wymusić określonej wersji, aby przeczytać `Serialize` funkcja klasy pochodnej.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#27](../../mfc/codesnippet/cpp/carchive-class_19.cpp)]

##  <a name="setstoreparams"></a>  CArchive::SetStoreParams

Użyj `SetStoreParams` w przypadku przechowywania dużej liczby `CObject`-pochodnych obiektów w archiwum.

```
void SetStoreParams(UINT nHashSize = 2053, UINT nBlockSize = 128);
```

### <a name="parameters"></a>Parametry

*nHashSize*<br/>
Rozmiar tablicy skrótów do wskaźnika interfejsu mapy. Musi być liczbą Północnej.

*nBlockSize*<br/>
Określa poziom szczegółowości alokacji pamięci do rozszerzania parametry. Powinien być potęgą liczby 2 w celu uzyskania najlepszej wydajności.

### <a name="remarks"></a>Uwagi

`SetStoreParams` Umożliwia ustawienie rozmiaru tabeli wyznaczania wartości skrótu i rozmiar bloku mapy, używany do identyfikowania następującą liczbę unikatowych obiektów podczas procesu serializacji.

Nie należy wywołać `SetStoreParams` po wszystkie obiekty są przechowywane lub po [MapObject](#mapobject) lub [SE operace WriteObject](#writeobject) jest wywoływana.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

##  <a name="write"></a>  CArchive::Write

Zapisuje określoną liczbę bajtów do archiwum.

```
void Write(const void* lpBuf, INT nMax);
```

### <a name="parameters"></a>Parametry

*lpBuf*<br/>
Wskaźnik do buforu dostarczone przez użytkownika, który zawiera dane do zapisania archiwum.

*nMax*<br/>
Liczba całkowita określająca liczbę bajtów do zapisania archiwum.

### <a name="remarks"></a>Uwagi

Archiwum nie formatuje bajtów.

Możesz użyć `Write` funkcja elementu członkowskiego, w ramach Twojej `Serialize` funkcję, aby napisać zwykłych struktur, które są zawarte w obiektów.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#23](../../mfc/codesnippet/cpp/carchive-class_20.cpp)]

##  <a name="writeclass"></a>  CArchive::WriteClass

Użyj `WriteClass` do przechowywania wersji i klasa informacji klasy bazowej podczas serializacji w klasie pochodnej.

```
void WriteClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>Parametry

*pClassRef*<br/>
Wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) strukturę, która odnosi się do żądanego odwołania do klasy.

### <a name="remarks"></a>Uwagi

`WriteClass` zapisuje odwołanie do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) dla klasy bazowej do `CArchive`. Użyj [CArchive::ReadClass](#readclass) można pobrać odwołania.

`WriteClass` sprawdza, czy informacje zarchiwizowanego klasy jest zgodny z klasy środowiska uruchomieniowego. Jeśli nie jest zgodny, `WriteClass` zgłosi [CArchiveException](../../mfc/reference/carchiveexception-class.md).

Należy użyć klasy środowiska uruchomieniowego [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) i [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); w przeciwnym razie `WriteClass` zgłosi [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Możesz użyć [SerializeClass](#serializeclass) zamiast `WriteClass`, która obsługuje Odczyt i zapis dla odwołania do klasy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#28](../../mfc/codesnippet/cpp/carchive-class_21.cpp)]

##  <a name="writeobject"></a>  CArchive::WriteObject

Zapisuje określony `CObject` do archiwum.

```
void WriteObject(const CObject* pOb);
```

### <a name="parameters"></a>Parametry

*pOb*<br/>
Stały wskaźnik do obiektu są przechowywane.

### <a name="remarks"></a>Uwagi

Ta funkcja jest zazwyczaj wywoływana `CArchive` wstawiania ( **<<**) operator jest przeciążony dla `CObject`. `WriteObject`, z kolei wywołuje `Serialize` funkcji klasy zarchiwizowane.

Musisz podać IMPLEMENT_SERIAL — makro do włączenia archiwizacji. `WriteObject` zapisuje nazwę klasy ASCII do archiwum. Ta nazwa klasy jest weryfikowana później, podczas procesu ładowania. Specjalne schemat kodowania zapobiega niepotrzebnego dublowania Nazwa klasy dla wielu obiektów klasy. Ten schemat zapobiega także nadmiarowym obiektów, które są celami więcej niż jeden wskaźnik.

Obiekt dokładnie encoding — metoda (w tym nazwę klasy ASCII) jest szczegółowo opisuje implementacja i może ulec zmianie w przyszłych wersjach biblioteki.

> [!NOTE]
>  Zakończ tworzenie, usuwanie i aktualizowanie wszystkich obiektów, przed rozpoczęciem ich archiwizowanie. Archiwum zostanie uszkodzona, po przemieszaniu archiwizowanie za pomocą modyfikacji obiektu.

### <a name="example"></a>Przykład

Aby uzyskać pełną definicję klasy `CAge`, zobacz przykład [CObList::CObList](../../mfc/reference/coblist-class.md#coblist).

[!code-cpp[NVC_MFCSerialization#29](../../mfc/codesnippet/cpp/carchive-class_22.cpp)]

##  <a name="writestring"></a>  CArchive::WriteString

Używaj tej funkcji elementu członkowskiego do zapisywania danych z bufora do pliku związanego z `CArchive` obiektu.

```
void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>Parametry

*lpsz*<br/>
Określa wskaźnik do buforu zawierające ciąg tekstowy zakończony znakiem null.

### <a name="remarks"></a>Uwagi

Kończącego znaku null ('\0') nie są zapisywane do pliku. nie jest nowym wierszem automatycznie zapisywane.

`WriteString` zgłasza wyjątek w odpowiedzi na kilka warunków, w tym warunku pełnego dysku.

`Write` jest również dostępna, ale zamiast kończące się na znaku null, zapisuje żądanej liczby bajtów do pliku.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCSerialization#30](../../mfc/codesnippet/cpp/carchive-class_23.cpp)]

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CFile](../../mfc/reference/cfile-class.md)<br/>
[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Klasa CSocket](../../mfc/reference/csocket-class.md)<br/>
[Klasa CSocketFile](../../mfc/reference/csocketfile-class.md)
