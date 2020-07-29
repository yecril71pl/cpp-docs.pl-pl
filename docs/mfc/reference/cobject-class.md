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
ms.openlocfilehash: ce745e0717e36a3c9acb5323d04545c59750add7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222904"
---
# <a name="cobject-class"></a>Klasa CObject

Główna Klasa bazowa dla biblioteka MFC.

## <a name="syntax"></a>Składnia

```
class AFX_NOVTABLE CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Nazwa|Opis|
|----------|-----------------|
|[CObject:: CObject](#cobject)|Konstruktor domyślny.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CObject:: AssertValid](#assertvalid)|Weryfikuje integralność tego obiektu.|
|[CObject::D UMP](#dump)|Tworzy zrzut diagnostyczny tego obiektu.|
|[CObject:: GetRuntimeClass](#getruntimeclass)|Zwraca `CRuntimeClass` strukturę odpowiadającą klasie tego obiektu.|
|[CObject:: IsKindOf](#iskindof)|Testuje relację tego obiektu z daną klasą.|
|[CObject:: isserializacja](#isserializable)|Testuje, czy ten obiekt może być serializowany.|
|[CObject:: serializować](#serialize)|Ładuje lub zapisuje obiekt z/do archiwum.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CObject:: operator — usuwanie](#operator_delete)|**`delete`** Operator specjalny.|
|[CObject:: operator new](#operator_new)|**`new`** Operator specjalny.|

## <a name="remarks"></a>Uwagi

Służy jako element główny nie tylko dla klas bibliotek, takich jak `CFile` i `CObList` , ale również dla klas, które można napisać. `CObject`oferuje podstawowe usługi, w tym

- Obsługa serializacji

- Informacje o klasie czasu wykonywania

- Dane wyjściowe diagnostyki obiektów

- Zgodność z klasami kolekcji

Należy pamiętać, że program nie `CObject` obsługuje dziedziczenia wielokrotnego. Klasy pochodne mogą mieć tylko jedną `CObject` klasę bazową i `CObject` muszą znajdować się po lewej stronie w hierarchii. Jest jednak dozwolone, aby struktury i niepochodne klasy były dostępne w oddziałach `CObject` z wieloma dziedziczeniem.

`CObject`W przypadku używania niektórych opcjonalnych makr w implementacji i deklaracjach klas można realizować Najważniejsze korzyści.

Makra pierwszego poziomu, [DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic) i [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic), umożliwiają dostęp w czasie wykonywania do nazwy klasy i jej pozycji w hierarchii. To z kolei umożliwia znaczący dumping diagnostyczny.

Makra drugiego poziomu, [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) i [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial), obejmują wszystkie funkcje makr pierwszego poziomu i umożliwiają "Serializowanie" obiektu do i z "archiwum".

Aby uzyskać informacje na temat ogólnego i używania klas Microsoft Foundation `CObject` , zobacz [Używanie CObject](../../mfc/using-cobject.md) i [serializacji](../../mfc/serialization-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CObject`

## <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

## <a name="cobjectassertvalid"></a><a name="assertvalid"></a>CObject:: AssertValid

Weryfikuje integralność tego obiektu.

```
virtual void AssertValid() const;
```

### <a name="remarks"></a>Uwagi

`AssertValid`sprawdza ważność tego obiektu, sprawdzając jego stan wewnętrzny. W wersji debugowania biblioteki program `AssertValid` może potwierdzić i w ten sposób przerwać program z komunikatem zawierającym numer wiersza i nazwę pliku, w którym potwierdzenie nie powiodło się.

Podczas pisania własnej klasy należy przesłonić `AssertValid` funkcję w celu zapewnienia usług diagnostycznych dla siebie i innych użytkowników klasy. Przesłonięte `AssertValid` zwykle wywołuje `AssertValid` funkcję swojej klasy bazowej przed sprawdzeniem składowych danych, które są unikatowe dla klasy pochodnej.

Ponieważ `AssertValid` jest **`const`** funkcją, nie można zmienić stanu obiektu podczas testu. Własne funkcje klasy pochodnej nie powinny zgłaszać wyjątków, ale raczej należy zastanowić się, `AssertValid` czy wykryją nieprawidłowe dane obiektu.

Definicja "ważność" zależy od klasy obiektu. Jako regułę, funkcja powinna wykonać "płytkie". Oznacza to, że jeśli obiekt zawiera wskaźniki do innych obiektów, powinien sprawdzić, czy wskaźniki nie mają wartości null, ale nie powinny wykonywać testów ważności na obiektach, do których odwołują się wskaźniki.

### <a name="example"></a>Przykład

Aby [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) uzyskać listę `CAge` klasy używanej we wszystkich przykładach, Zobacz CObList:: CObList `CObject` .

[!code-cpp[NVC_MFCCObjectSample#7](../../mfc/codesnippet/cpp/cobject-class_1.cpp)]

Aby uzyskać inny przykład, zobacz [AfxDoForAllObjects](diagnostic-services.md#afxdoforallobjects).

## <a name="cobjectcobject"></a><a name="cobject"></a>CObject:: CObject

Te funkcje są `CObject` konstruktorami standardowymi.

```
CObject();
CObject(const CObject& objectSrc);
```

### <a name="parameters"></a>Parametry

*objectSrc*<br/>
Odwołanie do innego`CObject`

### <a name="remarks"></a>Uwagi

Wersja domyślna jest automatycznie wywoływana przez konstruktora klasy pochodnej.

Jeśli klasa jest serializowana (obejmuje makro IMPLEMENT_SERIAL), wówczas w deklaracji klasy musi być używany Konstruktor domyślny (Konstruktor bez argumentów). Jeśli nie potrzebujesz domyślnego konstruktora, zadeklaruj prywatny lub chroniony Konstruktor "Empty". Aby uzyskać więcej informacji, zobacz [using CObject](../../mfc/using-cobject.md).

Standardowy Konstruktor kopiowania klas w języku C++ wykonuje kopię składową z elementu członkowskiego. Obecność prywatnego `CObject` konstruktora kopiującego gwarantuje komunikat o błędzie kompilatora, jeśli Konstruktor kopiujący klasy jest wymagany, ale nie jest dostępny. W związku z tym należy dostarczyć konstruktora kopiującego, jeśli Klasa wymaga tej funkcji.

### <a name="example"></a>Przykład

Aby uzyskać listę klasy użytej w przykładach, zobacz [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` `CObject` .

[!code-cpp[NVC_MFCCObjectSample#8](../../mfc/codesnippet/cpp/cobject-class_2.cpp)]

## <a name="cobjectdump"></a><a name="dump"></a>CObject::D UMP

Zrzuca zawartość obiektu do obiektu [CDumpContext](../../mfc/reference/cdumpcontext-class.md) .

```
virtual void Dump(CDumpContext& dc) const;
```

### <a name="parameters"></a>Parametry

*DC*<br/>
Kontekst zrzutu diagnostyki dla zatopienia, zazwyczaj `afxDump` .

### <a name="remarks"></a>Uwagi

Podczas pisania własnej klasy należy przesłonić `Dump` funkcję w celu zapewnienia usług diagnostycznych dla siebie i innych użytkowników klasy. Przesłonięte `Dump` zwykle wywołuje `Dump` funkcję swojej klasy bazowej przed przystąpieniem do drukowania składowych danych, które są unikatowe dla klasy pochodnej. `CObject::Dump`Drukuje nazwę klasy, jeśli Klasa używa `IMPLEMENT_DYNAMIC` makra lub IMPLEMENT_SERIAL.

> [!NOTE]
> `Dump`Funkcja nie powinna drukować znaku nowego wiersza na końcu danych wyjściowych.

`Dump`wywołania mają sens tylko w wersji debugowej biblioteka MFC. W **#ifdef _DEBUG** /  `#endif` przypadku kompilacji warunkowej należy odwoływać się do nawiasów, deklaracji funkcji i implementacji funkcji #ifdef _DEBUG.

Ponieważ `Dump` jest **`const`** funkcją, nie można zmienić stanu obiektu podczas zrzutu.

[Operator wstawiania CDumpContext (<<)](../../mfc/reference/cdumpcontext-class.md#operator_lt_lt) wywołuje, `Dump` gdy `CObject` wskaźnik zostanie wstawiony.

`Dump`zezwala tylko na "acykliczne" dumpingu obiektów. Można zrzucić listę obiektów, na przykład, jeśli jeden z obiektów jest samą listą, ostatecznie przepełni stos.

### <a name="example"></a>Przykład

Aby [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) uzyskać listę `CAge` klasy używanej we wszystkich przykładach, Zobacz CObList:: CObList `CObject` .

[!code-cpp[NVC_MFCCObjectSample#9](../../mfc/codesnippet/cpp/cobject-class_3.cpp)]

## <a name="cobjectgetruntimeclass"></a><a name="getruntimeclass"></a>CObject:: GetRuntimeClass

Zwraca `CRuntimeClass` strukturę odpowiadającą klasie tego obiektu.

```
virtual CRuntimeClass* GetRuntimeClass() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do struktury [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) odpowiadający klasie tego obiektu; nigdy nie **ma wartości null**.

### <a name="remarks"></a>Uwagi

Istnieje jedna `CRuntimeClass` Struktura dla każdej `CObject` klasy pochodnej. Elementy członkowskie struktury są następujące:

- **LPCSTR m_lpszClassName** Ciąg zakończony znakiem null zawierający nazwę klasy ASCII.

- **m_nObjectSize int** Rozmiar obiektu w bajtach. Jeśli obiekt ma elementy członkowskie danych wskazujące przydzieloną pamięć, rozmiar tej pamięci nie jest uwzględniany.

- **M_wSchema uint** Numer schematu (-1 dla klas, które nie są serializowane). Aby uzyskać opis numeru schematu, zobacz makro [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) .

- **CObject \* (Pascal \* m_pfnCreateObject) ()** wskaźnik funkcji do domyślnego konstruktora, który tworzy obiekt klasy (prawidłowy tylko wtedy, gdy klasa obsługuje tworzenie dynamiczne; w przeciwnym razie zwraca **wartość null**).

- **CRuntimeClass \* (Pascal \* m_pfn_GetBaseClass) ()** Jeśli aplikacja jest dynamicznie połączona z wersją AFXDLL MFC, wskaźnik do funkcji, która zwraca `CRuntimeClass` strukturę klasy bazowej.

- **CRuntimeClass \* m_pBaseClass** , jeśli aplikacja jest statycznie połączona z MFC, wskaźnikiem do `CRuntimeClass` struktury klasy bazowej.

Ta funkcja wymaga użycia makra [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic), [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)lub [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) w implementacji klasy. W przeciwnym razie otrzymasz nieprawidłowe wyniki.

### <a name="example"></a>Przykład

Aby [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) uzyskać listę `CAge` klasy używanej we wszystkich przykładach, Zobacz CObList:: CObList `CObject` .

[!code-cpp[NVC_MFCCObjectSample#10](../../mfc/codesnippet/cpp/cobject-class_4.cpp)]

## <a name="cobjectiskindof"></a><a name="iskindof"></a>CObject:: IsKindOf

Testuje relację tego obiektu z daną klasą.

```
BOOL IsKindOf(const CRuntimeClass* pClass) const;
```

### <a name="parameters"></a>Parametry

*pClass*<br/>
Wskaźnik do struktury [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) skojarzonej z `CObject` klasą pochodną.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli obiekt odpowiada klasie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja testuje *pClass* , aby zobaczyć, czy (1) jest obiektem określonej klasy lub (2) jest obiektem klasy pochodzącej od określonej klasy. Ta funkcja działa tylko dla klas zadeklarowanych za pomocą makra [DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic), [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate)lub [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) .

Nie używaj tej funkcji w szerokim stopniu, ponieważ obniża ona funkcję polimorfizmu języka C++. Zamiast tego użyj funkcji wirtualnych.

### <a name="example"></a>Przykład

Aby [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) uzyskać listę `CAge` klasy używanej we wszystkich przykładach, Zobacz CObList:: CObList `CObject` .

[!code-cpp[NVC_MFCCObjectSample#11](../../mfc/codesnippet/cpp/cobject-class_5.cpp)]

## <a name="cobjectisserializable"></a><a name="isserializable"></a>CObject:: isserializacja

Sprawdza, czy ten obiekt kwalifikuje się do serializacji.

```
BOOL IsSerializable() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli ten obiekt może być serializowany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby można było serializować klasę, jej Deklaracja musi zawierać [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) makro, a implementacja musi zawierać makro [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) .

> [!NOTE]
> Nie należy przesłaniać tej funkcji.

### <a name="example"></a>Przykład

Aby [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) uzyskać listę `CAge` klasy używanej we wszystkich przykładach, Zobacz CObList:: CObList `CObject` .

[!code-cpp[NVC_MFCCObjectSample#12](../../mfc/codesnippet/cpp/cobject-class_6.cpp)]

## <a name="cobjectoperator-delete"></a><a name="operator_delete"></a>CObject:: operator — usuwanie

Dla wydanej wersji biblioteki operator **`delete`** zwalnia pamięć przydzieloną przez operatora **`new`** .

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

W wersji Debug operator **`delete`** uczestniczy w schemacie monitorowania alokacji zaprojektowanym do wykrywania przecieków pamięci.

Jeśli używasz wiersza kodu

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

przed dowolnymi implementacjami w programie. Plik CPP, a następnie **`delete`** zostanie użyta trzecia wersja programu, która przechowuje nazwę pliku i numer wiersza w przydzielonym bloku na potrzeby późniejszego raportowania. Nie trzeba martwić się o dostarczenie dodatkowych parametrów; makro zajmie się tym, że.

Nawet jeśli nie używasz DEBUG_NEW w trybie debugowania, nadal będziesz mieć możliwość wykrywania przecieków, ale bez określonego powyżej raportowania liczby wierszy pliku źródłowego.

Jeśli zastąpisz operatory **`new`** i **`delete`** , ta możliwość diagnostyki zostanie utracona.

### <a name="example"></a>Przykład

Aby uzyskać listę klasy użytej w przykładach, zobacz [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` `CObject` .

[!code-cpp[NVC_MFCCObjectSample#15](../../mfc/codesnippet/cpp/cobject-class_8.cpp)]

## <a name="cobjectoperator-new"></a><a name="operator_new"></a>CObject:: operator new

W przypadku wersji biblioteki, operator **`new`** wykonuje optymalną alokację pamięci w sposób podobny do `malloc` .

```cpp
void* PASCAL operator new(size_t nSize);
void* PASCAL operator new(size_t, void* p);

void* PASCAL operator new(
    size_t nSize,
    LPCSTR lpszFileName,
    int nLine);
```

### <a name="remarks"></a>Uwagi

W wersji Debug operator **`new`** uczestniczy w schemacie monitorowania alokacji zaprojektowanym do wykrywania przecieków pamięci.

Jeśli używasz wiersza kodu

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

przed dowolnymi implementacjami w programie. Plik CPP, a następnie **`new`** zostanie użyta druga wersja programu, która przechowuje nazwę pliku i numer wiersza w przydzielonym bloku na potrzeby późniejszego raportowania. Nie trzeba martwić się o dostarczenie dodatkowych parametrów; makro zajmie się tym, że.

Nawet jeśli nie używasz DEBUG_NEW w trybie debugowania, nadal będziesz mieć możliwość wykrywania przecieków, ale bez określonego powyżej raportowania liczby wierszy pliku źródłowego.

> [!NOTE]
> W przypadku zastąpienia tego operatora należy również przesłonić **`delete`** . Nie należy używać standardowej funkcji biblioteki `_new_handler` .

### <a name="example"></a>Przykład

Aby uzyskać listę klasy użytej w przykładach, zobacz [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` `CObject` .

[!code-cpp[NVC_MFCCObjectSample#16](../../mfc/codesnippet/cpp/cobject-class_9.h)]

## <a name="cobjectserialize"></a><a name="serialize"></a>CObject:: serializować

Odczytuje lub zapisuje ten obiekt z lub do archiwum.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*ty*<br/>
`CArchive`Obiekt do serializacji do lub z.

### <a name="remarks"></a>Uwagi

Należy przesłonić `Serialize` dla każdej klasy, która ma zostać zserializowana. Zastąpiony `Serialize` musi najpierw wywołać `Serialize` funkcję swojej klasy bazowej.

Należy również użyć makra [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) w deklaracji klasy i należy użyć makra [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) w implementacji.

Użyj [CArchive:: IsLoading](../../mfc/reference/carchive-class.md#isloading) lub [CArchive:: isprzechowywanie](../../mfc/reference/carchive-class.md#isstoring) , aby określić, czy archiwum jest ładowane czy przechowywane.

`Serialize`jest wywoływany przez [CArchive:: ReadObject](../../mfc/reference/carchive-class.md#readobject) i [CArchive:: WriteObject](../../mfc/reference/carchive-class.md#writeobject). Te funkcje są skojarzone z `CArchive` operatorem wstawiania ( **<\<**) and extraction operator ( **>>** ).

Przykłady serializacji można znaleźć w artykule [serializacji artykułu: serializacji obiektu](../../mfc/serialization-serializing-an-object.md).

### <a name="example"></a>Przykład

Aby [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) uzyskać listę `CAge` klasy używanej we wszystkich przykładach, Zobacz CObList:: CObList `CObject` .

[!code-cpp[NVC_MFCCObjectSample#13](../../mfc/codesnippet/cpp/cobject-class_10.cpp)]

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)
