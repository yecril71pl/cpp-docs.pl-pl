---
title: "CArchive — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: aa6350a1195a0096160ab1c776009a3ac7a0e0d9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="carchive-class"></a>CArchive — klasa
Umożliwia zapisanie złożoną siecią obiektów w formularzu binarne stałych (zazwyczaj Magazyn dyskowy), który będzie nadal występować po usunięciu tych obiektów.  
  
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
|[CArchive::Abort](#abort)|Zamyka archiwum bez generowania wyjątku.|  
|[CArchive::Close](#close)|Liczba opróżnień niezapisanych danych i zakończy połączenie z `CFile`.|  
|[CArchive::Flush](#flush)|Liczba opróżnień niezapisanych danych z bufora archiwum.|  
|[CArchive::GetFile](#getfile)|Pobiera `CFile` wskaźnik do obiektu dla tego archiwum.|  
|[CArchive::GetObjectSchema](#getobjectschema)|Wywoływana z `Serialize` funkcji można ustalić wersji obiektu, który jest poddawany deserializacji.|  
|[CArchive::IsBufferEmpty](#isbufferempty)|Określa, czy podczas Windows Sockets został opróżniony buforu odbierania procesu.|  
|[CArchive::IsLoading](#isloading)|Określa, czy ładowanie jest archiwum.|  
|[CArchive::IsStoring](#isstoring)|Określa, czy jest przechowywanie archiwum.|  
|[CArchive::MapObject](#mapobject)|Umieszcza obiekty w tablicy nie są serializowane do pliku, ale które są dostępne dla podobiektów do odwołania.|  
|[CArchive::Read](#read)|Odczytuje raw bajtów.|  
|[CArchive::ReadClass](#readclass)|Odczyty odwołań do klas wcześniej zapisanych z `WriteClass`.|  
|[CArchive::ReadObject](#readobject)|Wywołuje obiekt `Serialize` funkcji do załadowania.|  
|[CArchive::ReadString](#readstring)|Odczytuje pojedynczy wiersz tekstu.|  
|[CArchive::SerializeClass](#serializeclass)|Odczytuje i zapisuje odwołania klasy do `CArchive` obiektu, w zależności od kierunku `CArchive`.|  
|[CArchive::SetLoadParams](#setloadparams)|Ustawia rozmiar, do którego zwiększania obciążenia tablicy. Musi zostać wywołana przed załadowaniem wszystkich obiektów lub przed `MapObject` lub `ReadObject` jest wywoływana.|  
|[CArchive::SetObjectSchema](#setobjectschema)|Ustawia schematu obiektu przechowywane w obiekcie archiwum.|  
|[CArchive::SetStoreParams](#setstoreparams)|Określa rozmiar tabeli wyznaczania wartości skrótu i rozmiar bloku mapy używany do identyfikowania obiektów unikatowy podczas serializacji.|  
|[CArchive::Write](#write)|Zapisuje nieprzetworzone bajtów.|  
|[CArchive::WriteClass](#writeclass)|Zapisuje odwołanie do `CRuntimeClass` do `CArchive`.|  
|[CArchive::WriteObject](#writeobject)|Wywołuje obiekt `Serialize` funkcji do przechowywania.|  
|[CArchive::WriteString](#writestring)|Zapisuje pojedynczy wiersz tekstu.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CArchive::operator&lt;&lt;](#operator_lt_lt)|Przechowuje obiekty i typy pierwotne do archiwum.|  
|[CArchive::operator&gt;&gt;](#operator_gt_gt)|Ładuje obiekty i typy pierwotne z archiwum.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CArchive::m_pDocument](#m_pdocument)||  
  
## <a name="remarks"></a>Uwagi  
 `CArchive`nie ma klasy podstawowej.  
  
 Później można ładować obiektów z magazynu trwałego przywracanie ich w pamięci. Ten proces polegający na wprowadzaniu danych trwałych jest nazywany "serializacji."  
  
 Można potraktować jako strumienia binarnego rodzaj obiektu archiwum. Jak strumień we/wy archiwum jest skojarzony z pliku i pozwala buforowanego zapisywanie i odczytywanie danych z magazynu. Sekwencje znaków ASCII przetwarza strumień wejścia/wyjścia, ale archiwum przetwarza dane obiektu binarnego w formacie wydajne, nonredundant.  
  
 Należy utworzyć [cfile —](../../mfc/reference/cfile-class.md) obiekt, aby można było utworzyć `CArchive` obiektu. Należy Ponadto upewnij się, że archiwum stan ładowania/magazynowania jest zgodna z trybu otwartego pliku. Jest ograniczona do jednej aktywnej archiwum dla każdego pliku.  
  
 Podczas konstruowania `CArchive` obiektu, dołącz je do obiektu klasy `CFile` (lub klasy pochodnej) reprezentujący plik. Możesz również określić, czy archiwum będą używane dla ładowania lub przechowywania. A `CArchive` obiektu może przetwarzać nie tylko typy pierwotne, ale także obiekty [CObject](../../mfc/reference/cobject-class.md)— przeznaczony do serializacji klas pochodnych. Klasy możliwej do serializacji ma zazwyczaj `Serialize` funkcji członkowskiej która zwykle używa [declare_serial —](../../mfc/reference/run-time-object-model-services.md#declare_serial) i [implement_serial —](../../mfc/reference/run-time-object-model-services.md#implement_serial) makra, zgodnie z opisem w klasie `CObject`.  
  
 Przeciążone wyodrębniania (  **>>** ) i wstawiania (  **<<** ) operatory są wygodne archiwum interfejsów programowania obsługujących obu typów pierwotnych i `CObject` -klas pochodnych.  
  
 `CArchive`obsługuje także programowania przy użyciu klas MFC Windows Sockets [CSocket —](../../mfc/reference/csocket-class.md) i [CSocketFile](../../mfc/reference/csocketfile-class.md). [IsBufferEmpty](#isbufferempty) funkcji członkowskiej obsługuje wykorzystanie.  
  
 Aby uzyskać więcej informacji na temat `CArchive`, zobacz artykuły [szeregowanie](../../mfc/serialization-in-mfc.md) i [Windows Sockets: przy użyciu gniazda z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CArchive`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h  
  
##  <a name="abort"></a>CArchive::Abort  
 Wywołanie tej funkcji, aby zamknąć archiwum bez generowania wyjątku.  
  
```  
void Abort ();
```  
  
### <a name="remarks"></a>Uwagi  
 **CArchive** zwykle wywoła destruktora **Zamknij**, która spowoduje to opróżnienie dowolne dane, które nie zostały zapisane do skojarzonego `CFile` obiektu. Może to spowodować wyjątków.  
  
 Przechwytywanie tych wyjątków, jest warto użyć **przerwać**, dzięki czemu destructing `CArchive` obiektu nie powoduje dalsze wyjątki. Podczas obsługi wyjątków, `CArchive::Abort` nie zgłosi wyjątku przy błędach ponieważ, w przeciwieństwie do [CArchive::Close](#close), **przerwać** ignoruje błędów.  
  
 Jeśli używasz **nowe** przydzielić `CArchive` obiektów na stercie, następnie należy ją usunąć po zamknięciu pliku.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CArchive::WriteClass](#writeclass).  
  
##  <a name="carchive"></a>CArchive::CArchive  
 Konstruuje `CArchive` obiektu i określa, czy będzie używana dla ładowania lub przechowywania obiektów.  
  
```  
CArchive(
    CFile* pFile,  
    UINT nMode,  
    int nBufSize = 4096,  
    void* lpBuf = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pFile`  
 Wskaźnik do `CFile` obiekt, który jest ultimate źródłowy lub docelowy trwałych danych.  
  
 `nMode`  
 Flaga określająca, czy obiekty zostaną załadowane z lub przechowywane do archiwum. `nMode` Parametr musi mieć jedną z następujących wartości:  
  
- **CArchive::load** ładuje dane z archiwum. Wymaga tylko `CFile` uprawnienia do odczytu.  
  
- **CArchive::store** zapisuje dane w archiwum. Wymaga `CFile` uprawnienie do zapisu.  
  
- **CArchive::bNoFlushOnDelete** uniemożliwia automatyczne wywoływanie archiwum `Flush` gdy jest wywoływana destruktor archiwum. Po ustawieniu ta flaga jest odpowiedzialny za jawnie podczas wywoływania **Zamknij** przed wywołaniem destruktor. W przeciwnym razie zostanie uszkodzone dane.  
  
 `nBufSize`  
 Liczba całkowita określająca rozmiar buforu wewnętrznego pliku w bajtach. Należy pamiętać, że domyślny rozmiar buforu 4096 bajtów. Jeśli regularnie archiwizowany dużych obiektów, umożliwi zwiększenie wydajności, jeśli używasz większy rozmiar buforu, który jest wielokrotnością rozmiaru buforu pliku.  
  
 `lpBuf`  
 Opcjonalnym wskaźnikiem bufor dostarczone przez użytkownika rozmiaru `nBufSize`. Jeśli nie określisz ten parametr, archiwum przydziela buforu z lokalnej sterty i zwalnia go, gdy obiekt zostanie zniszczony. Archiwum nie wolnego buforu dostarczone przez użytkownika.  
  
### <a name="remarks"></a>Uwagi  
 Określenie tej wartości nie można zmienić po utworzeniu archiwum.  
  
 Nie można używać `CFile` operacje, aby zmienić stan pliku do czasu zamknięcia archiwum. Działanie takie uszkodzą integralność archiwum. Użytkownik może uzyskać dostępu do położenia wskaźnika pliku w dowolnym momencie podczas serializacji, uzyskując obiektu pliku archiwum na podstawie [Pobieranie_pliku](#getfile) funkcji członkowskiej, a następnie użyć [CFile::GetPosition](../../mfc/reference/cfile-class.md#getposition) — funkcja . Należy wywołać [CArchive::Flush](#flush) przed uzyskaniem położenia wskaźnika pliku.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCSerialization#12](../../mfc/codesnippet/cpp/carchive-class_1.cpp)]  
  
##  <a name="close"></a>CArchive::Close  
 Liczba opróżnień żadnych danych pozostałych w buforze, zamyka archiwum i rozłącza archiwum z pliku.  
  
```  
void Close();
```  
  
### <a name="remarks"></a>Uwagi  
 Nie dalsze działania w archiwum są dozwolone. Po zamknięciu archiwum, można utworzyć innej archiwum dla tego samego pliku lub możesz zamknąć plik.  
  
 Funkcja członkowska **Zamknij** gwarantuje, że wszystkie dane są przesyłane z archiwum do pliku i jego powoduje, że archiwum. Aby przeprowadzić transferu z pliku na nośniku, należy najpierw użyć [CFile::Close](../../mfc/reference/cfile-class.md#close) , a następnie zniszcz `CFile` obiektu.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CArchive::WriteString](#writestring).  
  
##  <a name="flush"></a>CArchive::Flush  
 Wymusza pozostałych w buforze archiwum są zapisywane w pliku danych.  
  
```  
void Flush();
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska `Flush` gwarantuje, że wszystkie dane są przesyłane z archiwum do pliku. Należy wywołać [CFile::Close](../../mfc/reference/cfile-class.md#close) można zakończyć transferu z pliku na nośniku.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCSerialization#13](../../mfc/codesnippet/cpp/carchive-class_2.cpp)]  
  
##  <a name="getfile"></a>CArchive::GetFile  
 Pobiera `CFile` wskaźnik do obiektu dla tego archiwum.  
  
```  
CFile* GetFile() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Stała wskaźnika do `CFile` obiektu w użyciu.  
  
### <a name="remarks"></a>Uwagi  
 Należy opróżnić archiwum przed użyciem `GetFile`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCSerialization#14](../../mfc/codesnippet/cpp/carchive-class_3.cpp)]  
  
##  <a name="getobjectschema"></a>CArchive::GetObjectSchema  
 Wywołanie tej funkcji z `Serialize` funkcji można ustalić wersji obiektu, który jest poddawany deserializacji.  
  
```  
UINT GetObjectSchema();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Podczas deserializacji, wersja obiektu odczytu.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji jest prawidłowa tylko gdy `CArchive` obiektu jest ładowany ( [CArchive::IsLoading](#isloading) zwraca różną od zera). Powinna to być pierwsze wywołanie w `Serialize` funkcji i wywołana tylko raz. Zwracana wartość ( **UINT**) -1 oznacza, że numer wersji jest nieznany.  
  
 A `CObject`— Klasa pochodna może używać **versionable_schema —** łączyć (przy użyciu alternatywy bitowej `OR`) ze schematem w wersji samej (w `IMPLEMENT_SERIAL` makro) można utworzyć "znalezienie, obiektu" oznacza to, którego `Serialize` funkcji członkowskiej może być odczytany wiele wersji. Domyślna funkcjonalność framework (bez **versionable_schema —**) jest do zgłoszenia wyjątku, gdy wersja jest niezgodna.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCSerialization#15](../../mfc/codesnippet/cpp/carchive-class_4.cpp)]  
  
##  <a name="isbufferempty"></a>CArchive::IsBufferEmpty  
 Wywołanie tej funkcji elementu członkowskiego, aby określić, czy bufor wewnętrzny obiekt archiwum jest pusty.  
  
```  
BOOL IsBufferEmpty() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli bufor archiwum jest pusta. w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest dostarczany do obsługi programowania za pomocą klasy MFC Windows Sockets `CSocketFile`. Nie trzeba używać go do archiwum skojarzone z `CFile` obiektu.  
  
 Przyczyna przy użyciu `IsBufferEmpty` z archiwum skojarzone z `CSocketFile` obiekt jest, że bufor archiwum może zawierać więcej niż jednego komunikatu lub rekordu. Po otrzymaniu jeden komunikat, należy użyć `IsBufferEmpty` do kontrolowania pętli, które nadal odbieranie danych, dopóki bufor jest pusty. Aby uzyskać więcej informacji, zobacz [Receive](../../mfc/reference/casyncsocket-class.md#receive) funkcji członkowskiej klasy `CAsyncSocket`, która przedstawia sposób użycia `IsBufferEmpty`.  
  
 Aby uzyskać więcej informacji, zobacz [Windows Sockets: przy użyciu gniazda z archiwami](../../mfc/windows-sockets-using-sockets-with-archives.md).  
  
##  <a name="isloading"></a>CArchive::IsLoading  
 Określa, czy archiwum podczas ładowania danych.  
  
```  
BOOL IsLoading() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, gdy archiwum jest obecnie używana do załadowania; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska jest wywoływana przez `Serialize` funkcje klasy zarchiwizowane.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCSerialization#16](../../mfc/codesnippet/cpp/carchive-class_5.cpp)]  
  
##  <a name="isstoring"></a>CArchive::IsStoring  
 Określa, czy archiwum są przechowywane dane.  
  
```  
BOOL IsStoring() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, gdy archiwum jest aktualnie używany do przechowywania; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja członkowska jest wywoływana przez `Serialize` funkcje klasy zarchiwizowane.  
  
 Jeśli `IsStoring` stan archiwum jest różna od zera, a następnie jego `IsLoading` stan ma wartość 0 i na odwrót.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCSerialization#17](../../mfc/codesnippet/cpp/carchive-class_6.cpp)]  
  
##  <a name="mapobject"></a>CArchive::MapObject  
 Wywołanie tej funkcji członkowskich można umieścić na mapie, które nie są naprawdę serializowane do pliku, ale które są dostępne dla podobiektów odwoływać się do obiektów.  
  
```  
void MapObject(const CObject* pOb);
```  
  
### <a name="parameters"></a>Parametry  
 `pOb`  
 Stała wskaźnika do obiektu są przechowywane.  
  
### <a name="remarks"></a>Uwagi  
 Na przykład dokument nie może serializować, ale może serializować elementy, które są częścią dokumentu. Wywołując `MapObject`, musisz zezwolić na te elementy lub podobiektów do odwołania dokumentu. Ponadto może serializować serializacji podelementy ich `m_pDocument` wskaźnik Wstecz.  
  
 Możesz wywołać `MapObject` podczas Przechowaj i załadować z `CArchive` obiektu. `MapObject`Dodaje określony obiekt do struktur danych wewnętrznych obsługiwanego przez `CArchive` obiektu podczas serializacji i deserializacji, lecz w odróżnieniu od [funkcji ReadObject](#readobject) i [metody WriteObject](#writeobject) **,** nie wywołuje serializacji obiektu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCSerialization#18](../../mfc/codesnippet/cpp/carchive-class_7.h)]  
  
 [!code-cpp[NVC_MFCSerialization#19](../../mfc/codesnippet/cpp/carchive-class_8.cpp)]  
  
 [!code-cpp[NVC_MFCSerialization#20](../../mfc/codesnippet/cpp/carchive-class_9.h)]  
  
 [!code-cpp[NVC_MFCSerialization#21](../../mfc/codesnippet/cpp/carchive-class_10.cpp)]  
  
##  <a name="m_pdocument"></a>CArchive::m_pDocument  
 Ustaw **NULL** domyślnie ten wskaźnik do **CDocument** można ustawić na inny użytkownik `CArchive` wystąpienie chce.  
  
```  
CDocument* m_pDocument;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typowe użycie ten wskaźnik jest w celu przekazania dodatkowych informacji na temat procesu serializacji dla wszystkich obiektów serializowana. Jest to osiągane przez inicjowanie wskaźnik z dokumentu ( **CDocument**-klasy) które jest serializowana, w taki sposób, że obiektów w tym dokumencie miał dostęp do dokumentu w razie potrzeby. Ten wskaźnik jest już używana przez `COleClientItem` obiekty podczas serializacji.  
  
 Ustawia framework `m_pDocument` do dokumentu poddany serializacji, gdy użytkownik generuje plik otworzyć lub zapisać polecenia. Jeśli serializacji obiektu łączenie i osadzanie (OLE) dokumentu kontenera przyczyn innych niż Otwórz lub Zapisz, musisz jawnie ustawić `m_pDocument`. Na przykład można to zrobić podczas serializowania dokumentu kontenera do Schowka.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCSerialization#35](../../mfc/codesnippet/cpp/carchive-class_11.cpp)]  
  
##  <a name="operator_lt_lt"></a>CArchive::operator&lt;&lt;  
 Przechowuje wskazanego obiektu lub typu pierwotnego do archiwum.  
  
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
 A `CArchive` odwołania, który umożliwia wielu operatorów wstawiania w jednym wierszu.  
  
### <a name="remarks"></a>Uwagi  
 Ostatnie są dwie wersje powyżej specjalnie z myślą o przechowywaniu 64-bitowych liczb całkowitych.  
  
 Jeśli używasz `IMPLEMENT_SERIAL` makra w implementacji klasy, a następnie operator wstawiania przeciążenie `CObject` wywołuje chronionej **metody WriteObject**. Ta funkcja jest z kolei wywołuje `Serialize` funkcji klasy.  
  
 [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) operatora wstawiania (<<) obsługuje diagnostycznych zrzucanie i zapisywanie do archiwum.  
  
### <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono użycie `CArchive` operator wstawiania << z `int` i `long` typów.  
  
 [!code-cpp[NVC_MFCSerialization#31](../../mfc/codesnippet/cpp/carchive-class_12.cpp)]  
  
### <a name="example"></a>Przykład  
 W tym przykładzie 2 zademonstrowano użycie `CArchive` operator wstawiania << z `CStringT` typu.  
  
 [!code-cpp[NVC_MFCSerialization#32](../../mfc/codesnippet/cpp/carchive-class_13.cpp)]  
  
##  <a name="operator_gt_gt"></a>CArchive::operator&gt;&gt;  
 Ładuje wskazanego obiektu lub typu pierwotnego z archiwum.  
  
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
 A `CArchive` odwołania, który umożliwia wielu operatorów wyodrębniania w jednym wierszu.  
  
### <a name="remarks"></a>Uwagi  
 Ostatnie są dwie wersje powyżej specjalnie z myślą o ładowania 64-bitowych liczb całkowitych.  
  
 Jeśli używasz `IMPLEMENT_SERIAL` makra w implementacji klasy, a następnie operatorów wyodrębniania przeciążenie `CObject` wywołać chronionej **funkcji ReadObject** — funkcja (za pomocą wskaźnika niezerową klasie czasu wykonywania). Ta funkcja jest z kolei wywołuje `Serialize` funkcji klasy.  
  
 [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) operatorów wyodrębniania (>>) obsługuje ładowanie z archiwum.  
  
### <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono użycie `CArchive` operator wyodrębniania >> z `int` typu.  
  
 [!code-cpp[NVC_MFCSerialization#33](../../mfc/codesnippet/cpp/carchive-class_14.cpp)]  
  
### <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono użycie `CArchive` operatorów wstawiania i wyodrębniania <\< i >> z `CStringT` typu.  
  
 [!code-cpp[NVC_MFCSerialization#34](../../mfc/codesnippet/cpp/carchive-class_15.cpp)]  
  
##  <a name="read"></a>CArchive::Read  
 Odczytuje określoną liczbę bajtów z archiwum.  
  
```  
UINT Read(void* lpBuf, UINT nMax);
```  
  
### <a name="parameters"></a>Parametry  
 `lpBuf`  
 Wskaźnik do buforu dostarczone przez użytkownika, który będzie odbierać dane odczytywane z archiwum.  
  
 `nMax`  
 Bez znaku liczba całkowita określająca liczbę bajtów do odczytu z archiwum.  
  
### <a name="return-value"></a>Wartość zwracana  
 Całkowitą bez znaku, zawierającą liczbę bajtów odczytanych w rzeczywistości. Jeśli wartość zwracana jest mniejsza niż żądana, osiągnięto koniec pliku. Nie wyjątek pod warunkiem końca pliku.  
  
### <a name="remarks"></a>Uwagi  
 Archiwum nie ma możliwości interpretowania bajtów.  
  
 Można użyć **odczytu** funkcji Członkowskich w Twojej `Serialize` funkcji do odczytywania zwykłej struktury, które są zawarte w obiektów.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCSerialization#24](../../mfc/codesnippet/cpp/carchive-class_16.cpp)]  
  
##  <a name="readclass"></a>CArchive::ReadClass  
 Wywołanie tej funkcji Członkowskich odczytać odwołanie do klasy wcześniej zapisanych z [WriteClass](#writeclass).  
  
```  
CRuntimeClass* ReadClass(
    const CRuntimeClass* pClassRefRequested = NULL,  
    UINT* pSchema = NULL,  
    DWORD* pObTag = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pClassRefRequested`  
 Wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) struktura umożliwiająca żądanego odwołania do klasy. Może być **NULL**.  
  
 `pSchema`  
 Wskaźnik do schematu o klasie czasu wykonywania wcześniej przechowywane.  
  
 `pObTag`  
 Liczba, która odwołuje się do obiektu unikatowy tag. Używana wewnętrznie przez implementację [funkcji ReadObject](#readobject). Widoczne zaawansowane programowania. `pObTag` zwykle powinny być **NULL**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) struktury.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `pClassRefRequested` nie jest **NULL**, `ReadClass` sprawdza, czy informacje o klasie zarchiwizowane jest zgodne z klasy środowiska wykonawczego. Jeśli nie jest zgodny, `ReadClass` zgłosi [CArchiveException](../../mfc/reference/carchiveexception-class.md).  
  
 Należy użyć klasy środowiska uruchomieniowego [declare_serial —](../../mfc/reference/run-time-object-model-services.md#declare_serial) i [implement_serial —](../../mfc/reference/run-time-object-model-services.md#implement_serial); w przeciwnym razie `ReadClass` zgłosi [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).  
  
 Jeśli `pSchema` jest **NULL**, można pobrać schematu klasy przechowywanych przez wywołanie metody [CArchive::GetObjectSchema](#getobjectschema); w przeciwnym razie  **\***  `pSchema`będzie zawierać schemat klasie czasu wykonywania, które wcześniej były przechowywane.  
  
 Można użyć [SerializeClass](#serializeclass) zamiast `ReadClass`, który obsługuje odczytywanie i zapisywanie odwołania do klasy.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CArchive::WriteClass](#writeclass).  
  
##  <a name="readobject"></a>CArchive::ReadObject  
 Odczytuje dane obiektu z archiwum i tworzy obiekt odpowiedniego typu.  
  
```  
CObject* ReadObject(const CRuntimeClass* pClass);
```  
  
### <a name="parameters"></a>Parametry  
 `pClass`  
 Stała wskaźnika do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) strukturę, która odnosi się do obiektu, oczekiwany Odczyt.  
  
### <a name="return-value"></a>Wartość zwracana  
 A [CObject](../../mfc/reference/cobject-class.md) wskaźnika, który musi być bezpiecznie rzutowany na prawidłowe pochodnej klasy przy użyciu [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof).  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest zazwyczaj wywoływana `CArchive` wyodrębniania (  **>>** ) przeciążenie operatora [CObject](../../mfc/reference/cobject-class.md) wskaźnika. **Funkcji ReadObject**, z kolei wywołuje `Serialize` funkcja zarchiwizowane klasy.  
  
 Jeśli podasz niezerową `pClass` parametr, który można uzyskać przez [runtime_class —](../../mfc/reference/run-time-object-model-services.md#runtime_class) makra, a następnie funkcja sprawdza, czy klasa czasu wykonywania zarchiwizowane obiektu. Założono, że użyto `IMPLEMENT_SERIAL` makra w implementacji klasy.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CArchive::WriteObject](#writeobject).  
  
##  <a name="readstring"></a>CArchive::ReadString  
 Wywołanie tej funkcji członkowskich można odczytać danych tekstu w buforze z pliku skojarzone z `CArchive` obiektu.  
  
```  
BOOL ReadString(CString& rString); 
LPTSTR ReadString(LPTSTR lpsz, UINT nMax);
```  
  
### <a name="parameters"></a>Parametry  
 `rString`  
 Odwołanie do [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) po jest do odczytu z pliku skojarzone z obiektem CArchive będzie zawierające ciąg wynikowy.  
  
 `lpsz`  
 Określa wskaźnik do buforu dostarczone przez użytkownika, który będzie otrzymywał ciąg tekstowy zerem.  
  
 `nMax`  
 Określa maksymalną liczbę znaków do odczytania. Powinien być mniejszy niż rozmiar *lpsz* buforu.  
  
### <a name="return-value"></a>Wartość zwracana  
 W wersji, która zwraca **BOOL**, **TRUE** w przypadku powodzenia; **FALSE** inaczej.  
  
 W wersji, która zwraca `LPTSTR`, wskaźnik w buforze zawierające dane tekstowe; **NULL** czy osiągnięto koniec pliku.  
  
### <a name="remarks"></a>Uwagi  
 W bieżącej wersji funkcji członkowskiej z `nMax` parametru, buforu zmieści do limitu `nMax` - 1 znaków. Odczytywanie została zatrzymana przez parę wysuwu wiersza powrotu karetki. Zawsze są usuwane znakami nowego wiersza. Znak null ('\0') jest dołączany w każdym przypadku.  
  
 [CArchive::Read](#read) jest również dostępna dla danych wejściowych w trybie tekstowym, ale nie zakończy na parę wysuwu wiersza powrotu karetki.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CArchive::WriteString](#writestring).  
  
##  <a name="serializeclass"></a>CArchive::SerializeClass  
 Wywołania funkcji członkowskiej, gdy chcesz przechowywać i załadować informacji o wersji klasy podstawowej.  
  
```  
void SerializeClass(const CRuntimeClass* pClassRef);
```  
  
### <a name="parameters"></a>Parametry  
 `pClassRef`  
 Wskaźnik do obiektu środowiska wykonawczego klasy dla klasy podstawowej.  
  
### <a name="remarks"></a>Uwagi  
 `SerializeClass`Odwołanie do klasy zapisuje lub odczytuje `CArchive` obiektu, w zależności od kierunku `CArchive`. Użyj `SerializeClass` zamiast [ReadClass](#readclass) i [WriteClass](#writeclass) to wygodny sposób, aby serializować obiektów klasy podstawowej; `SerializeClass` wymaga mniej kodu i mniej parametrów.  
  
 Podobnie jak `ReadClass`, `SerializeClass` sprawdza, czy informacje o klasie zarchiwizowane jest zgodne z klasy środowiska wykonawczego. Jeśli nie jest zgodny, `SerializeClass` zgłosi [CArchiveException](../../mfc/reference/carchiveexception-class.md).  
  
 Należy użyć klasy środowiska uruchomieniowego [declare_serial —](../../mfc/reference/run-time-object-model-services.md#declare_serial) i [implement_serial —](../../mfc/reference/run-time-object-model-services.md#implement_serial); w przeciwnym razie `SerializeClass` zgłosi [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).  
  
 Użyj [runtime_class —](../../mfc/reference/run-time-object-model-services.md#runtime_class) makra, aby pobrać wartość `pRuntimeClass` parametru. Klasa podstawowa musi mieć używany [implement_serial —](../../mfc/reference/run-time-object-model-services.md#implement_serial) makra.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCSerialization#25](../../mfc/codesnippet/cpp/carchive-class_17.h)]  
  
##  <a name="setloadparams"></a>CArchive::SetLoadParams  
 Wywołanie `SetLoadParams` gdy ma dużą liczbę do odczytu `CObject`-pochodną obiekty archiwum.  
  
```  
void SetLoadParams(UINT nGrowBy = 1024);
```  
  
### <a name="parameters"></a>Parametry  
 `nGrowBy`  
 Minimalna liczba gniazd elementu można przydzielić, jeśli konieczne jest zwiększenie rozmiaru.  
  
### <a name="remarks"></a>Uwagi  
 `CArchive`używa tablicy obciążenia do rozpoznania odwołania do obiektów przechowywanych w archiwum. `SetLoadParams`Umożliwia ustawienie rozmiaru, do którego zwiększania obciążenia tablicy.  
  
 Nie należy wywołać `SetLoadParams` po załadowaniu dowolnego obiektu lub po [MapObject](#mapobject) lub [funkcji ReadObject](#readobject) jest wywoływana.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]  
  
##  <a name="setobjectschema"></a>CArchive::SetObjectSchema  
 Wywołanie tej funkcji członkowskich można ustawić przechowywane w obiekcie archiwum do schematu obiektu `nSchema`.  
  
```  
void SetObjectSchema(UINT nSchema);
```  
  
### <a name="parameters"></a>Parametry  
 `nSchema`  
 Określa schematu obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Następne wywołanie [GetObjectSchema](#getobjectschema) zwróci wartość przechowywana we `nSchema`.  
  
 Użyj `SetObjectSchema` dla zaawansowanych wersji; na przykład, gdy chcesz wymusić określonej wersji, aby przeczytać `Serialize` funkcji klasy pochodnej.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCSerialization#27](../../mfc/codesnippet/cpp/carchive-class_19.cpp)]  
  
##  <a name="setstoreparams"></a>CArchive::SetStoreParams  
 Użyj `SetStoreParams` w przypadku przechowywania dużej liczby `CObject`-pochodnych obiektów w archiwum.  
  
```  
void SetStoreParams(UINT nHashSize = 2053, UINT nBlockSize = 128);
```  
  
### <a name="parameters"></a>Parametry  
 *nHashSize*  
 Rozmiar tablicy skrótów do wskaźnika interfejsu mapy. Musi być liczbą pierwsze.  
  
 `nBlockSize`  
 Określa stopień szczegółowości Alokacja pamięci dla Rozszerzanie parametrów. Powinien być potęgą liczby 2, aby uzyskać najlepszą wydajność.  
  
### <a name="remarks"></a>Uwagi  
 `SetStoreParams`Umożliwia ustawienie rozmiaru tabeli wyznaczania wartości skrótu i rozmiar bloku mapy używany do identyfikowania obiektów unikatowy podczas serializacji.  
  
 Nie należy wywołać `SetStoreParams` po wszystkie obiekty są przechowywane lub po [MapObject](#mapobject) lub [metody WriteObject](#writeobject) jest wywoływana.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]  
  
##  <a name="write"></a>CArchive::Write  
 Zapisuje określoną liczbę bajtów do archiwum.  
  
```  
void Write(const void* lpBuf, INT nMax);
```  
  
### <a name="parameters"></a>Parametry  
 `lpBuf`  
 Wskaźnik do buforu dostarczone przez użytkownika, który zawiera dane do zapisania do archiwum.  
  
 `nMax`  
 Liczba całkowita określająca liczbę bajtów do zapisania do archiwum.  
  
### <a name="remarks"></a>Uwagi  
 Archiwum nie formatuje liczby bajtów.  
  
 Można użyć **zapisu** funkcji Członkowskich w Twojej `Serialize` funkcja zapisu zwykłych struktury, które są zawarte w obiektów.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCSerialization#23](../../mfc/codesnippet/cpp/carchive-class_20.cpp)]  
  
##  <a name="writeclass"></a>CArchive::WriteClass  
 Użyj `WriteClass` do przechowywania wersji, a klasa informacji klasy podstawowej podczas serializacji klasy pochodnej.  
  
```  
void WriteClass(const CRuntimeClass* pClassRef);
```  
  
### <a name="parameters"></a>Parametry  
 `pClassRef`  
 Wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) struktura umożliwiająca żądanego odwołania do klasy.  
  
### <a name="remarks"></a>Uwagi  
 `WriteClass`zapisuje odwołanie do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) dla klasy podstawowej na `CArchive`. Użyj [CArchive::ReadClass](#readclass) można pobrać odwołania.  
  
 `WriteClass`sprawdza, czy informacje o klasie zarchiwizowane jest zgodny z klasy środowiska wykonawczego. Jeśli nie jest zgodny, `WriteClass` zgłosi [CArchiveException](../../mfc/reference/carchiveexception-class.md).  
  
 Należy użyć klasy środowiska uruchomieniowego [declare_serial —](../../mfc/reference/run-time-object-model-services.md#declare_serial) i [implement_serial —](../../mfc/reference/run-time-object-model-services.md#implement_serial); w przeciwnym razie `WriteClass` zgłosi [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).  
  
 Można użyć [SerializeClass](#serializeclass) zamiast `WriteClass`, który obsługuje odczytywanie i zapisywanie odwołania do klasy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCSerialization#28](../../mfc/codesnippet/cpp/carchive-class_21.cpp)]  
  
##  <a name="writeobject"></a>CArchive::WriteObject  
 Zapisuje określony `CObject` do archiwum.  
  
```  
void WriteObject(const CObject* pOb);
```  
  
### <a name="parameters"></a>Parametry  
 `pOb`  
 Stała wskaźnika do obiektu są przechowywane.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest zazwyczaj wywoływana `CArchive` wstawiania (  **<<** ) przeciążenie operatora `CObject`. **Metody WriteObject**, z kolei wywołuje `Serialize` funkcja zarchiwizowane klasy.  
  
 Należy użyć `IMPLEMENT_SERIAL` makro do włączenia archiwizacji. **Metody WriteObject** zapisuje nazwy klasy ASCII do archiwum. Ta nazwa klasy jest weryfikowana później, podczas procesu ładowania. Specjalne schemat kodowania zapobiega niepotrzebnego dublowania Nazwa klasy dla wielu obiektów klasy. Ten schemat uniemożliwia także programowi magazynu geograficznie nadmiarowego obiektów, które są elementy docelowe więcej niż jednego wskaźnika.  
  
 Obiekt dokładne kodowanie — metoda (w tym nazwę klasy ASCII) jest szczegółów implementacji i może ulec zmianie w przyszłych wersjach biblioteki.  
  
> [!NOTE]
>  Zakończ tworzenie, usuwanie i aktualizowanie wszystkich obiektów, przed rozpoczęciem ich archiwizacji. Archiwum zostanie uszkodzony, jeśli można mieszać archiwizacji modyfikacji obiektu.  
  
### <a name="example"></a>Przykład  
 Aby uzyskać definicję klasy `CAge`, zobacz przykład [CObList::CObList](../../mfc/reference/coblist-class.md#coblist).  
  
 [!code-cpp[NVC_MFCSerialization#29](../../mfc/codesnippet/cpp/carchive-class_22.cpp)]  
  
##  <a name="writestring"></a>CArchive::WriteString  
 Ta funkcja elementu członkowskiego służy do zapisywania danych z bufora do pliku związanego z `CArchive` obiektu.  
  
```  
void WriteString(LPCTSTR lpsz);
```  
  
### <a name="parameters"></a>Parametry  
 `lpsz`  
 Określa wskaźnik do buforu, zawierające ciąg tekstowy zerem.  
  
### <a name="remarks"></a>Uwagi  
 Znak końcowy null ('\0') nie są zapisywane do pliku. nie jest nowym wierszem automatycznie zapisane.  
  
 `WriteString`zgłasza wyjątek w odpowiedzi na kilka warunków, w tym warunku pełnej dysku.  
  
 **Zapis** jest również dostępny, ale zamiast kończące się na znak null, zapisuje żądanej liczby bajtów do pliku.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCSerialization#30](../../mfc/codesnippet/cpp/carchive-class_23.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Cfile — klasa](../../mfc/reference/cfile-class.md)   
 [CObject — klasa](../../mfc/reference/cobject-class.md)   
 [CSocket — klasa](../../mfc/reference/csocket-class.md)   
 [Klasa CSocketFile](../../mfc/reference/csocketfile-class.md)
