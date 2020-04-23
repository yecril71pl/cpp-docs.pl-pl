---
title: Klasa CObject
ms.date: 11/04/2016
f1_keywords:
- CObject
- AFX/CObject
- AFX/CObject::CObject
- AFX/CObject::AssertValid
- AFX/CObject::Dump
- AFX/CObject::GetRuntimeClass
- AFX/CObject::IsKindOf
- AFX/CObject::IsSerializable
- AFX/CObject::Serialize
helpviewer_keywords:
- CObject [MFC], CObject
- CObject [MFC], AssertValid
- CObject [MFC], Dump
- CObject [MFC], GetRuntimeClass
- CObject [MFC], IsKindOf
- CObject [MFC], IsSerializable
- CObject [MFC], Serialize
ms.assetid: 95e9acd3-d9eb-4ac0-b52b-ca4a501a7a3a
ms.openlocfilehash: 66d76e0062d13b2bd5a16d9b07f99db9e989805a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753995"
---
# <a name="cobject-class"></a>Klasa CObject

Główna klasa podstawowa biblioteki klas programu Microsoft Foundation.

## <a name="syntax"></a>Składnia

```
class AFX_NOVTABLE CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[CObject::CObject](#cobject)|Domyślny konstruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CObject::AssertValid](#assertvalid)|Sprawdza poprawność integralności tego obiektu.|
|[CObject::Dump](#dump)|Tworzy zrzut diagnostyczny tego obiektu.|
|[CObject::GetRuntimeClass](#getruntimeclass)|Zwraca `CRuntimeClass` strukturę odpowiadającą klasie tego obiektu.|
|[CObject::IsKindOf](#iskindof)|Testuje relację tego obiektu z daną klasą.|
|[CObject::IsSerializable](#isserializable)|Testy, aby zobaczyć, czy ten obiekt może być serializowany.|
|[CObject::Serialize](#serialize)|Ładuje lub przechowuje obiekt z/do archiwum.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CObject::operator delete](#operator_delete)|Specjalny operator **usuwania.**|
|[CObject::operator nowy](#operator_new)|Specjalny **nowy** operator.|

## <a name="remarks"></a>Uwagi

Służy jako korzeń nie tylko dla `CFile` `CObList`klas biblioteki, takich jak i , ale także dla klas, które piszesz. `CObject`świadczy podstawowe usługi, w tym

- Obsługa serializacji

- Informacje o klasie w czasie wykonywania

- Wyjście diagnostyczne obiektu

- Zgodność z klasami kolekcji

Należy `CObject` zauważyć, że nie obsługuje wielu dziedziczenia. Klasy pochodne mogą mieć `CObject` tylko jedną `CObject` klasę podstawową i która musi znajdować się po lewej stronie w hierarchii. Jest jednak dopuszczalne, aby mieć struktury i nie- `CObject`-pochodne klasy w prawej części wielu segmentów dziedziczenia.

Zdasz sobie sprawę `CObject` z głównych korzyści z wyprowadzania, jeśli używasz niektórych opcjonalnych makr w implementacji klasy i deklaracji.

Makra pierwszego poziomu, [DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic) i [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic), umożliwiają dostęp w czasie wykonywania do nazwy klasy i jej pozycji w hierarchii. To z kolei pozwala na sensowny dumping diagnostyczny.

Makra drugiego poziomu, [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) i [IMPLEMENT_SERIAL,](run-time-object-model-services.md#implement_serial)zawierają wszystkie funkcje makr pierwszego poziomu i umożliwiają "serializowanie" obiektu do i z "archiwum".

Aby uzyskać informacje na temat wyprowadzania klas programu `CObject`Microsoft Foundation i klas C++ w ogóle i używania , zobacz [Korzystanie z CObject](../../mfc/using-cobject.md) i [Serialization](../../mfc/serialization-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CObject`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="cobjectassertvalid"></a><a name="assertvalid"></a>CObject::AssertValid

Sprawdza poprawność integralności tego obiektu.

```
virtual void AssertValid() const;
```

### <a name="remarks"></a>Uwagi

`AssertValid`przeprowadza sprawdzanie ważności tego obiektu, sprawdzając jego stan wewnętrzny. W wersji debugowania biblioteki może dochodzić i w ten sposób zakończyć program z komunikatem, który zawiera numer wiersza i nazwę pliku, `AssertValid` w którym twierdzenie nie powiodło się.

Podczas pisania własnej klasy, należy zastąpić `AssertValid` funkcję, aby zapewnić usługi diagnostyczne dla siebie i innych użytkowników klasy. Overridden `AssertValid` zwykle wywołuje `AssertValid` funkcję swojej klasy podstawowej przed sprawdzeniem elementów członkowskich danych unikatowych dla klasy pochodnej.

Ponieważ `AssertValid` jest **const** funkcji, nie mogą zmienić stan obiektu podczas testu. Własne funkcje `AssertValid` klasy pochodnej nie powinny zgłaszać wyjątków, ale raczej powinny potwierdzać, czy wykrywają nieprawidłowe dane obiektu.

Definicja "ważności" zależy od klasy obiektu. Z reguły funkcja powinna wykonywać "płytkie sprawdzanie". Oznacza to, że jeśli obiekt zawiera wskaźniki do innych obiektów, należy sprawdzić, czy wskaźniki nie są null, ale nie należy wykonywać badania ważności na obiekty, o których mowa w wskaźników.

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) dla listy `CAge` klasy używane `CObject` we wszystkich przykładach.

[!code-cpp[NVC_MFCCObjectSample#7](../../mfc/codesnippet/cpp/cobject-class_1.cpp)]

Inny przykład można znaleźć w [pliku AfxDoForAllObjects](diagnostic-services.md#afxdoforallobjects).

## <a name="cobjectcobject"></a><a name="cobject"></a>CObject::CObject

Funkcje te `CObject` są standardowe konstruktory.

```
CObject();
CObject(const CObject& objectSrc);
```

### <a name="parameters"></a>Parametry

*objectSrc*<br/>
Odniesienie do innego`CObject`

### <a name="remarks"></a>Uwagi

Wersja domyślna jest automatycznie wywoływana przez konstruktora klasy pochodnej.

Jeśli klasa jest serializable (zawiera IMPLEMENT_SERIAL makra), a następnie musi mieć domyślny konstruktor (konstruktor bez argumentów) w deklaracji klasy. Jeśli nie potrzebujesz domyślnego konstruktora, zadeklaruj prywatny lub chroniony konstruktor "pusty". Aby uzyskać więcej informacji, zobacz [Korzystanie z CObject](../../mfc/using-cobject.md).

Standardowy konstruktor kopii klasy domyślnej języka C++ wykonuje kopię typu element członkowski. Obecność konstruktora kopii prywatnej `CObject` gwarantuje komunikat o błędzie kompilatora, jeśli konstruktor kopii klasy jest potrzebne, ale nie jest dostępny. W związku z tym należy podać konstruktora kopii, jeśli klasa wymaga tej możliwości.

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) dla listy `CAge` klasy używane `CObject` w przykładach.

[!code-cpp[NVC_MFCCObjectSample#8](../../mfc/codesnippet/cpp/cobject-class_2.cpp)]

## <a name="cobjectdump"></a><a name="dump"></a>CObject::Dump

Zrzuca zawartość obiektu do obiektu [CDumpContext.](../../mfc/reference/cdumpcontext-class.md)

```
virtual void Dump(CDumpContext& dc) const;
```

### <a name="parameters"></a>Parametry

*Dc*<br/>
Kontekst zrzutu diagnostycznego `afxDump`do dumpingu, zwykle .

### <a name="remarks"></a>Uwagi

Podczas pisania własnej klasy, należy zastąpić `Dump` funkcję, aby zapewnić usługi diagnostyczne dla siebie i innych użytkowników klasy. Overridden `Dump` zwykle wywołuje `Dump` funkcję swojej klasy podstawowej przed drukowaniem elementów członkowskich danych unikatowych dla klasy pochodnej. `CObject::Dump`drukuje nazwę klasy, jeśli klasa `IMPLEMENT_DYNAMIC` używa makra lub IMPLEMENT_SERIAL.

> [!NOTE]
> Funkcja `Dump` nie powinna drukować znaku nowego elementu na końcu jego danych wyjściowych.

`Dump`wywołania mają sens tylko w wersji debugowania biblioteki klas programu Microsoft Foundation. Należy nawias wywołań, deklaracje funkcji i implementacje funkcji z **#ifdef _DEBUG** /  `#endif` instrukcji dla kompilacji warunkowej.

Ponieważ `Dump` jest **const** funkcji, nie mogą zmieniać stan obiektu podczas zrzutu.

[Operator wstawiania CDumpContext (<<)](../../mfc/reference/cdumpcontext-class.md#operator_lt_lt) `Dump` wywołuje `CObject` po wstawieniu wskaźnika.

`Dump`pozwala jedynie na "acykliczne" zatapianie przedmiotów. Można zrzucić listę obiektów, na przykład, ale jeśli jeden z obiektów jest sama lista, po pewnym czasie przepełnienie stosu.

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) dla listy `CAge` klasy używane `CObject` we wszystkich przykładach.

[!code-cpp[NVC_MFCCObjectSample#9](../../mfc/codesnippet/cpp/cobject-class_3.cpp)]

## <a name="cobjectgetruntimeclass"></a><a name="getruntimeclass"></a>CObject::GetRuntimeClass

Zwraca `CRuntimeClass` strukturę odpowiadającą klasie tego obiektu.

```
virtual CRuntimeClass* GetRuntimeClass() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) struktury odpowiadającej tej klasy obiektu; nigdy **NULL**.

### <a name="remarks"></a>Uwagi

Istnieje jedna `CRuntimeClass` struktura `CObject`dla każdej klasy pochodnej. Elementy członkowskie struktury są następujące:

- **m_lpszClassName LPCSTR** Ciąg zakończony z wartością null zawierający nazwę klasy ASCII.

- **int m_nObjectSize** Rozmiar obiektu w bajtach. Jeśli obiekt ma elementy członkowskie danych, które wskazują na przydzieloną pamięć, rozmiar tej pamięci nie jest uwzględniony.

- **m_wSchema UINT** Numer schematu ( - 1 dla klas nienaserializacyjnych). Opis numeru schematu można znaleźć w [makrze IMPLEMENT_SERIAL.](run-time-object-model-services.md#implement_serial)

- **CObject\* (\* PASCAL m_pfnCreateObject )( )** Wskaźnik funkcji do domyślnego konstruktora, który tworzy obiekt klasy (jest prawidłowy tylko wtedy, gdy klasa obsługuje dynamiczne tworzenie; w przeciwnym razie zwraca **wartość NULL**).

- **CRuntimeClass\* (\* PASCAL m_pfn_GetBaseClass )( )** Jeśli aplikacja jest dynamicznie połączony z afxdll wersji MFC, `CRuntimeClass` wskaźnik do funkcji, która zwraca strukturę klasy podstawowej.

- **CRuntimeClass\* m_pBaseClass** Jeśli aplikacja jest statycznie połączone z MFC, `CRuntimeClass` wskaźnik do struktury klasy podstawowej.

Ta funkcja wymaga użycia [makra IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic), [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)lub [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) w implementacji klasy. W przeciwnym razie otrzymasz nieprawidłowe wyniki.

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) dla listy `CAge` klasy używane `CObject` we wszystkich przykładach.

[!code-cpp[NVC_MFCCObjectSample#10](../../mfc/codesnippet/cpp/cobject-class_4.cpp)]

## <a name="cobjectiskindof"></a><a name="iskindof"></a>CObject::IsKindOf

Testuje relację tego obiektu z daną klasą.

```
BOOL IsKindOf(const CRuntimeClass* pClass) const;
```

### <a name="parameters"></a>Parametry

*pClass (klasa pClass)*<br/>
Wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) struktury skojarzone `CObject`z klasy pochodnej.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli obiekt odpowiada klasie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja testuje *pClass,* aby sprawdzić, czy (1) jest obiektem określonej klasy lub (2) jest obiektem klasy pochodnej określonej klasy. Ta funkcja działa tylko dla klas zadeklarowanych za pomocą [makra DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic) [, DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate)lub [DECLARE_SERIAL.](run-time-object-model-services.md#declare_serial)

Nie należy używać tej funkcji szeroko, ponieważ pokonuje funkcję polimorfizmu C++. Zamiast tego użyj funkcji wirtualnych.

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) dla listy `CAge` klasy używane `CObject` we wszystkich przykładach.

[!code-cpp[NVC_MFCCObjectSample#11](../../mfc/codesnippet/cpp/cobject-class_5.cpp)]

## <a name="cobjectisserializable"></a><a name="isserializable"></a>CObject::IsSerializable

Sprawdza, czy ten obiekt kwalifikuje się do serializacji.

```
BOOL IsSerializable() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli ten obiekt może być serializowany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby klasa była serializable, jego deklaracja musi zawierać [makro DECLARE_SERIAL,](run-time-object-model-services.md#declare_serial) a implementacja musi zawierać [makro IMPLEMENT_SERIAL.](run-time-object-model-services.md#implement_serial)

> [!NOTE]
> Nie należy zastępować tej funkcji.

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) dla listy `CAge` klasy używane `CObject` we wszystkich przykładach.

[!code-cpp[NVC_MFCCObjectSample#12](../../mfc/codesnippet/cpp/cobject-class_6.cpp)]

## <a name="cobjectoperator-delete"></a><a name="operator_delete"></a>CObject::operator delete

W przypadku wersji wydania biblioteki, operator **usuwa zwolnić** pamięć przydzieloną przez operatora **nowy**.

```cpp
void PASCAL operator delete(void* p);

void PASCAL operator delete(
    void* p,
    void* pPlace);

void PASCAL operator delete(
    void* p,
    LPCSTR lpszFileName,
    int nLine);
```

### <a name="remarks"></a>Uwagi

W wersji debugowania **delete** operatora uczestniczy w schemat monitorowania alokacji przeznaczony do wykrywania przecieków pamięci.

Jeśli używasz wiersza kodu

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

przed jakimkolwiek z implementacji w pliku . Plik CPP, a następnie trzecia wersja **delete** będą używane, przechowywanie nazwy pliku i numer wiersza w przydzielonym bloku do późniejszego raportowania. Nie musisz się martwić o podanie dodatkowych parametrów; makro dba o to za Ciebie.

Nawet jeśli nie używasz DEBUG_NEW w trybie debugowania, nadal otrzymasz wykrywanie przecieków, ale bez raportowania numerów wiersza pliku źródłowego opisanych powyżej.

Jeśli zastąpisz operatory **nowe** i **usuń,** utracisz tę funkcję diagnostyczną.

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) dla listy `CAge` klasy używane `CObject` w przykładach.

[!code-cpp[NVC_MFCCObjectSample#15](../../mfc/codesnippet/cpp/cobject-class_8.cpp)]

## <a name="cobjectoperator-new"></a><a name="operator_new"></a>CObject::operator nowy

W przypadku wersji biblioteki operator **new** wykonuje optymalną alokację `malloc`pamięci w sposób podobny do .

```cpp
void* PASCAL operator new(size_t nSize);
void* PASCAL operator new(size_t, void* p);

void* PASCAL operator new(
    size_t nSize,
    LPCSTR lpszFileName,
    int nLine);
```

### <a name="remarks"></a>Uwagi

W wersji debugowania **operator nowy** uczestniczy w schemat monitorowania alokacji przeznaczony do wykrywania przecieków pamięci.

Jeśli używasz wiersza kodu

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

przed jakimkolwiek z implementacji w pliku . Plik CPP, a następnie druga wersja **nowego** będą używane, przechowywanie nazwy pliku i numer wiersza w przydzielonym bloku do późniejszego raportowania. Nie musisz się martwić o podanie dodatkowych parametrów; makro dba o to za Ciebie.

Nawet jeśli nie używasz DEBUG_NEW w trybie debugowania, nadal otrzymasz wykrywanie przecieków, ale bez raportowania numerów wiersza pliku źródłowego opisanych powyżej.

> [!NOTE]
> W przypadku zastąpienia tego operatora należy również zastąpić **polecenie delete**. Nie należy używać `_new_handler` funkcji biblioteki standardowej.

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) dla listy `CAge` klasy używane `CObject` w przykładach.

[!code-cpp[NVC_MFCCObjectSample#16](../../mfc/codesnippet/cpp/cobject-class_9.h)]

## <a name="cobjectserialize"></a><a name="serialize"></a>CObject::Serialize

Odczytuje lub zapisuje ten obiekt z lub do archiwum.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*Ar*<br/>
Obiekt `CArchive` do serializacji do lub z.

### <a name="remarks"></a>Uwagi

Należy zastąpić `Serialize` dla każdej klasy, które mają być serializować. Overridden `Serialize` musi najpierw `Serialize` wywołać funkcję jego klasy podstawowej.

Należy również użyć [makra DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) w deklaracji klasy i należy użyć [makra IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) w implementacji.

Użyj [CArchive::IsLoading](../../mfc/reference/carchive-class.md#isloading) lub [CArchive::IsStoring,](../../mfc/reference/carchive-class.md#isstoring) aby ustalić, czy archiwum jest ładowanie lub przechowywanie.

`Serialize`jest wywoływana przez [CArchive::ReadObject](../../mfc/reference/carchive-class.md#readobject) i [CArchive::WriteObject](../../mfc/reference/carchive-class.md#writeobject). Funkcje te są `CArchive` skojarzone z ** < **operatorem wstawiania ( ) i operatorem ekstrakcji ( **>>**).

Przykłady serializacji można znaleźć w artykule [Serializacja: Serializacja obiektu](../../mfc/serialization-serializing-an-object.md).

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) dla listy `CAge` klasy używane `CObject` we wszystkich przykładach.

[!code-cpp[NVC_MFCCObjectSample#13](../../mfc/codesnippet/cpp/cobject-class_10.cpp)]

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)
