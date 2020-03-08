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
ms.openlocfilehash: 515c4e90ee6ab77a6c7c1ae108393ea1aafb7c17
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855328"
---
# <a name="cobject-class"></a>Klasa CObject

Główna Klasa bazowa dla biblioteka MFC.

## <a name="syntax"></a>Składnia

```
class AFX_NOVTABLE CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="protected-constructors"></a>Konstruktory chronione

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CObject:: CObject](#cobject)|Konstruktor domyślny.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CObject:: AssertValid](#assertvalid)|Weryfikuje integralność tego obiektu.|
|[CObject::D UMP](#dump)|Tworzy zrzut diagnostyczny tego obiektu.|
|[CObject:: GetRuntimeClass](#getruntimeclass)|Zwraca strukturę `CRuntimeClass` odpowiadającą klasie tego obiektu.|
|[CObject:: IsKindOf](#iskindof)|Testuje relację tego obiektu z daną klasą.|
|[CObject:: isserializacja](#isserializable)|Testuje, czy ten obiekt może być serializowany.|
|[CObject:: serializować](#serialize)|Ładuje lub zapisuje obiekt z/do archiwum.|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CObject:: operator — usuwanie](#operator_delete)|Operator **usuwania** specjalnego.|
|[CObject:: operator new](#operator_new)|Specjalny operator **New** .|

## <a name="remarks"></a>Uwagi

Służy jako element główny nie tylko dla klas biblioteki, takich jak `CFile` i `CObList`, ale również dla klas, które można napisać. `CObject` oferuje podstawowe usługi, w tym

- Obsługa serializacji

- Informacje o klasie czasu wykonywania

- Dane wyjściowe diagnostyki obiektów

- Zgodność z klasami kolekcji

Należy pamiętać, że `CObject` nie obsługuje dziedziczenia wielokrotnego. Klasy pochodne mogą mieć tylko jedną `CObject` klasę bazową, a `CObject` musi być lewej strony w hierarchii. Możliwe jest jednak, aby struktury i klasy pochodne inne niż `CObject`w oddziałach z wieloma dziedziczeniem z prawej strony.

W przypadku korzystania z niektórych opcjonalnych makr w implementacji i deklaracjach klas należy realizować Najważniejsze korzyści z `CObject` wyprowadzenia.

Makra pierwszego poziomu, [DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic) i [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic), umożliwiają dostęp w czasie wykonywania do nazwy klasy i jej pozycji w hierarchii. To z kolei umożliwia znaczący dumping diagnostyczny.

Makra drugiego poziomu, [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) i [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial), obejmują wszystkie funkcje makr pierwszego poziomu i umożliwiają "Serializowanie" obiektu do i z "archiwum".

Informacje o C++ [wykorzystaniu](../../mfc/using-cobject.md) klas i klas programu Microsoft Foundation ogólnie i przy użyciu `CObject`można znaleźć w temacie using CObject and [Serialization](../../mfc/serialization-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CObject`

## <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

##  <a name="assertvalid"></a>CObject:: AssertValid

Weryfikuje integralność tego obiektu.

```
virtual void AssertValid() const;
```

### <a name="remarks"></a>Uwagi

`AssertValid` sprawdza ważność tego obiektu, sprawdzając jego stan wewnętrzny. W wersji debugowanej biblioteki `AssertValid` może potwierdzić i zakończyć działanie programu z komunikatem zawierającym numer wiersza i nazwę pliku, w którym potwierdzenie nie powiodło się.

Podczas pisania własnej klasy należy zastąpić funkcję `AssertValid`, aby zapewnić usługi diagnostyczne dla siebie i innych użytkowników klasy. Zastąpiony `AssertValid` zwykle wywołuje funkcję `AssertValid` swojej klasy podstawowej przed sprawdzeniem, czy elementy członkowskie danych są unikatowe dla klasy pochodnej.

Ponieważ `AssertValid` jest funkcją **stałą** , nie można zmienić stanu obiektu podczas testu. Własne klasy pochodne `AssertValid` funkcje nie powinny zgłaszać wyjątków, ale raczej należy zastanowić się, czy wykryją nieprawidłowe dane obiektu.

Definicja "ważność" zależy od klasy obiektu. Jako regułę, funkcja powinna wykonać "płytkie". Oznacza to, że jeśli obiekt zawiera wskaźniki do innych obiektów, powinien sprawdzić, czy wskaźniki nie mają wartości null, ale nie powinny wykonywać testów ważności na obiektach, do których odwołują się wskaźniki.

### <a name="example"></a>Przykład

Zobacz [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) , aby zapoznać się z listą klasy `CAge` używanej we wszystkich `CObject` przykładach.

[!code-cpp[NVC_MFCCObjectSample#7](../../mfc/codesnippet/cpp/cobject-class_1.cpp)]

Aby uzyskać inny przykład, zobacz [AfxDoForAllObjects](diagnostic-services.md#afxdoforallobjects).

##  <a name="cobject"></a>CObject:: CObject

Te funkcje są standardowymi konstruktorami `CObject`.

```
CObject();
CObject(const CObject& objectSrc);
```

### <a name="parameters"></a>Parametry

*objectSrc*<br/>
Odwołanie do innego `CObject`

### <a name="remarks"></a>Uwagi

Wersja domyślna jest automatycznie wywoływana przez konstruktora klasy pochodnej.

Jeśli klasa jest serializowana (obejmuje makro IMPLEMENT_SERIAL), wówczas w deklaracji klasy musi być używany Konstruktor domyślny (Konstruktor bez argumentów). Jeśli nie potrzebujesz domyślnego konstruktora, zadeklaruj prywatny lub chroniony Konstruktor "Empty". Aby uzyskać więcej informacji, zobacz [using CObject](../../mfc/using-cobject.md).

Standardowy Konstruktor C++ kopiujący klasy standardowej wykonuje kopię składową z elementu członkowskiego. Obecność prywatnego konstruktora kopiującego `CObject` gwarantuje komunikat błędu kompilatora, jeśli Konstruktor kopiujący klasy jest wymagany, ale nie jest dostępny. W związku z tym należy dostarczyć konstruktora kopiującego, jeśli Klasa wymaga tej funkcji.

### <a name="example"></a>Przykład

Zobacz [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) , aby zapoznać się z listą klasy `CAge` używanej w przykładach `CObject`.

[!code-cpp[NVC_MFCCObjectSample#8](../../mfc/codesnippet/cpp/cobject-class_2.cpp)]

##  <a name="dump"></a>CObject::D UMP

Zrzuca zawartość obiektu do obiektu [CDumpContext](../../mfc/reference/cdumpcontext-class.md) .

```
virtual void Dump(CDumpContext& dc) const;
```

### <a name="parameters"></a>Parametry

*DC*<br/>
Kontekst zrzutu diagnostyki dla zatopienia, zwykle `afxDump`.

### <a name="remarks"></a>Uwagi

Podczas pisania własnej klasy należy zastąpić funkcję `Dump`, aby zapewnić usługi diagnostyczne dla siebie i innych użytkowników klasy. Zastąpiony `Dump` zwykle wywołuje funkcję `Dump` swojej klasy bazowej przed drukowaniem elementów członkowskich danych unikatowych dla klasy pochodnej. `CObject::Dump` drukuje nazwę klasy, jeśli Klasa używa makra `IMPLEMENT_DYNAMIC` lub IMPLEMENT_SERIAL.

> [!NOTE]
>  Funkcja `Dump` nie powinna drukować znaku nowego wiersza na końcu danych wyjściowych.

wywołania `Dump` są sensowne tylko w wersji Debug biblioteka MFC. W przypadku kompilacji warunkowej należy odwoływać się do nawiasów, deklaracji funkcji i implementacji funkcji **#ifdef _DEBUG**/ `#endif`.

Ponieważ `Dump` jest funkcją **stałą** , nie można zmienić stanu obiektu podczas zrzutu.

Wywołania [operatora wstawiania CDumpContext (< <)](../../mfc/reference/cdumpcontext-class.md#operator_lt_lt) `Dump`, gdy zostanie wstawiony wskaźnik `CObject`.

`Dump` zezwala tylko na "acykliczne" zatopienia obiektów. Można zrzucić listę obiektów, na przykład, jeśli jeden z obiektów jest samą listą, ostatecznie przepełni stos.

### <a name="example"></a>Przykład

Zobacz [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) , aby zapoznać się z listą klasy `CAge` używanej we wszystkich `CObject` przykładach.

[!code-cpp[NVC_MFCCObjectSample#9](../../mfc/codesnippet/cpp/cobject-class_3.cpp)]

##  <a name="getruntimeclass"></a>CObject:: GetRuntimeClass

Zwraca strukturę `CRuntimeClass` odpowiadającą klasie tego obiektu.

```
virtual CRuntimeClass* GetRuntimeClass() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do struktury [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) odpowiadający klasie tego obiektu; nigdy nie **ma wartości null**.

### <a name="remarks"></a>Uwagi

Dla każdej klasy pochodnej `CObject`istnieje jedna struktura `CRuntimeClass`. Elementy członkowskie struktury są następujące:

- **LPCSTR m_lpszClassName** Ciąg zakończony znakiem null zawierający nazwę klasy ASCII.

- **m_nObjectSize int** Rozmiar obiektu w bajtach. Jeśli obiekt ma elementy członkowskie danych wskazujące przydzieloną pamięć, rozmiar tej pamięci nie jest uwzględniany.

- **M_wSchema uint** Numer schematu (-1 dla klas, które nie są serializowane). Aby uzyskać opis numeru schematu, zobacz makro [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) .

- **CObject\* (PASCAL\* m_pfnCreateObject) ()** Wskaźnik funkcji do domyślnego konstruktora, który tworzy obiekt klasy (prawidłowy tylko wtedy, gdy klasa obsługuje tworzenie dynamiczne; w przeciwnym razie zwraca **wartość null**).

- **CRuntimeClass\* (PASCAL\* m_pfn_GetBaseClass) ()** Jeśli aplikacja jest dynamicznie połączona z wersją AFXDLL MFC, wskaźnik do funkcji, która zwraca strukturę `CRuntimeClass` klasy bazowej.

- **CRuntimeClass\* m_pBaseClass** Jeśli aplikacja jest statycznie połączona z MFC, wskaźnik do struktury `CRuntimeClass` klasy bazowej.

Ta funkcja wymaga użycia makra [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic), [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)lub [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) w implementacji klasy. W przeciwnym razie otrzymasz nieprawidłowe wyniki.

### <a name="example"></a>Przykład

Zobacz [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) , aby zapoznać się z listą klasy `CAge` używanej we wszystkich `CObject` przykładach.

[!code-cpp[NVC_MFCCObjectSample#10](../../mfc/codesnippet/cpp/cobject-class_4.cpp)]

##  <a name="iskindof"></a>CObject:: IsKindOf

Testuje relację tego obiektu z daną klasą.

```
BOOL IsKindOf(const CRuntimeClass* pClass) const;
```

### <a name="parameters"></a>Parametry

*pClass*<br/>
Wskaźnik do struktury [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) skojarzonej z klasą pochodną `CObject`.

### <a name="return-value"></a>Wartość zwracana

Różne od zera, jeśli obiekt odpowiada klasie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja testuje *pClass* , aby zobaczyć, czy (1) jest obiektem określonej klasy lub (2) jest obiektem klasy pochodzącej od określonej klasy. Ta funkcja działa tylko dla klas zadeklarowanych za pomocą makra [DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic), [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate)lub [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) .

Nie używaj tej funkcji w szerokim stopniu, C++ ponieważ obniża ona funkcję polimorfizmu. Zamiast tego użyj funkcji wirtualnych.

### <a name="example"></a>Przykład

Zobacz [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) , aby zapoznać się z listą klasy `CAge` używanej we wszystkich `CObject` przykładach.

[!code-cpp[NVC_MFCCObjectSample#11](../../mfc/codesnippet/cpp/cobject-class_5.cpp)]

##  <a name="isserializable"></a>CObject:: isserializacja

Sprawdza, czy ten obiekt kwalifikuje się do serializacji.

```
BOOL IsSerializable() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli ten obiekt może być serializowany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby można było serializować klasę, jej Deklaracja musi zawierać [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) makro, a implementacja musi zawierać makro [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) .

> [!NOTE]
>  Nie należy przesłaniać tej funkcji.

### <a name="example"></a>Przykład

Zobacz [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) , aby zapoznać się z listą klasy `CAge` używanej we wszystkich `CObject` przykładach.

[!code-cpp[NVC_MFCCObjectSample#12](../../mfc/codesnippet/cpp/cobject-class_6.cpp)]

##  <a name="operator_delete"></a>CObject:: operator — usuwanie

W wersji wydanej biblioteki operator **delete** zwalnia pamięć przydzieloną przez operatora **New**.

```
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

W wersji Debug operator **delete** uczestniczy w schemacie monitorowania alokacji zaprojektowanym do wykrywania przecieków pamięci.

Jeśli używasz wiersza kodu

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

przed dowolnymi implementacjami w programie. Plik CPP, a następnie zostanie użyta trzecia wersja narzędzia **delete** , która przechowuje nazwę pliku i numer wiersza w przydzielonym bloku na potrzeby późniejszego raportowania. Nie trzeba martwić się o dostarczenie dodatkowych parametrów; makro zajmie się tym, że.

Nawet jeśli nie używasz DEBUG_NEW w trybie debugowania, nadal będziesz mieć możliwość wykrywania przecieków, ale bez określonego powyżej raportowania liczby wierszy pliku źródłowego.

Jeśli zastąpisz operatory **New** i **delete**, ta możliwość diagnostyki zostanie utracona.

### <a name="example"></a>Przykład

Zobacz [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) , aby zapoznać się z listą klasy `CAge` używanej w przykładach `CObject`.

[!code-cpp[NVC_MFCCObjectSample#15](../../mfc/codesnippet/cpp/cobject-class_8.cpp)]

##  <a name="operator_new"></a>CObject:: operator new

Dla wydanej wersji biblioteki operator **New** wykonuje optymalną alokację pamięci w sposób podobny do `malloc`.

```
void* PASCAL operator new(size_t nSize);
void* PASCAL operator new(size_t, void* p);

void* PASCAL operator new(
    size_t nSize,
    LPCSTR lpszFileName,
    int nLine);
```

### <a name="remarks"></a>Uwagi

W wersji do debugowania operator **New** uczestniczy w schemacie monitorowania alokacji zaprojektowanym do wykrywania przecieków pamięci.

Jeśli używasz wiersza kodu

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

przed dowolnymi implementacjami w programie. Plik CPP, a następnie zostanie użyta druga wersja **nowego** , przechowująca nazwę pliku i numer wiersza w przydzielonym bloku na potrzeby późniejszego raportowania. Nie trzeba martwić się o dostarczenie dodatkowych parametrów; makro zajmie się tym, że.

Nawet jeśli nie używasz DEBUG_NEW w trybie debugowania, nadal będziesz mieć możliwość wykrywania przecieków, ale bez określonego powyżej raportowania liczby wierszy pliku źródłowego.

> [!NOTE]
>  W przypadku zastąpienia tego operatora należy również zastąpić **delete**. Nie należy używać standardowej funkcji `_new_handler` biblioteki.

### <a name="example"></a>Przykład

Zobacz [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) , aby zapoznać się z listą klasy `CAge` używanej w przykładach `CObject`.

[!code-cpp[NVC_MFCCObjectSample#16](../../mfc/codesnippet/cpp/cobject-class_9.h)]

##  <a name="serialize"></a>CObject:: serializować

Odczytuje lub zapisuje ten obiekt z lub do archiwum.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*ty*<br/>
Obiekt `CArchive` do serializacji do lub z.

### <a name="remarks"></a>Uwagi

Należy przesłonić `Serialize` dla każdej klasy, która ma zostać zserializowana. Zastąpiony `Serialize` musi najpierw wywołać funkcję `Serialize` swojej klasy bazowej.

Należy również użyć makra [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) w deklaracji klasy i należy użyć makra [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) w implementacji.

Użyj [CArchive:: IsLoading](../../mfc/reference/carchive-class.md#isloading) lub [CArchive:: isprzechowywanie](../../mfc/reference/carchive-class.md#isstoring) , aby określić, czy archiwum jest ładowane czy przechowywane.

`Serialize` jest wywoływany przez [CArchive:: ReadObject](../../mfc/reference/carchive-class.md#readobject) i [CArchive:: WriteObject](../../mfc/reference/carchive-class.md#writeobject). Te funkcje są skojarzone z operatorem wstawiania `CArchive` ( **<\<** ) i operatorem wyodrębniania ( **>>** ).

Przykłady serializacji można znaleźć w artykule [serializacji artykułu: serializacji obiektu](../../mfc/serialization-serializing-an-object.md).

### <a name="example"></a>Przykład

Zobacz [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) , aby zapoznać się z listą klasy `CAge` używanej we wszystkich `CObject` przykładach.

[!code-cpp[NVC_MFCCObjectSample#13](../../mfc/codesnippet/cpp/cobject-class_10.cpp)]

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)
