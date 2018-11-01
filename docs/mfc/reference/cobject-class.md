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
ms.openlocfilehash: eb0580f6fef39df29d66e15cfd051a0460cb8d56
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584018"
---
# <a name="cobject-class"></a>Klasa CObject

Główna klasa bazowa dla biblioteki klas Microsoft Foundation.

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
|[CObject::AssertValid](#assertvalid)|Weryfikuje integralność tego obiektu.|
|[CObject::Dump](#dump)|Tworzy diagnostycznych zrzutu tego obiektu.|
|[CObject::GetRuntimeClass](#getruntimeclass)|Zwraca `CRuntimeClass` struktury odpowiadający klasy tego obiektu.|
|[CObject::IsKindOf](#iskindof)|Testy tego obiektu relacji do danej klasy.|
|[CObject::IsSerializable](#isserializable)|Testy, aby zobaczyć, czy ten obiekt może być serializowany.|
|[CObject::Serialize](#serialize)|Ładuje i przechowuje obiekt z i do archiwum.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Usuń CObject::operator](#operator_delete)|Specjalne **Usuń** operatora.|
|[Nowe CObject::operator](#operator_new)|Specjalne **nowe** operatora.|

## <a name="remarks"></a>Uwagi

Służy ona jako katalog główny nie tylko dla biblioteki klas takich jak `CFile` i `CObList`, ale również dla klas, które piszesz. `CObject` oferuje podstawowe usługi, w tym

- Obsługa serializacji

- Informacje o klasie czasu wykonywania

- Diagnostyczne dane wyjściowe obiektu

- Zgodność z klasy kolekcji

Należy pamiętać, że `CObject` nie obsługują wielokrotnego dziedziczenia. Twoje klasy pochodne mogą mieć tylko jedną `CObject` klasy bazowej, a `CObject` musi być skrajnie po lewej stronie w hierarchii. Jest dozwolone, ale mają struktury i innych niż- `CObject`-klasy pochodne w po prawej stronie gałęzie dziedziczenia wielokrotnego.

Spowoduje więc duże korzyści z `CObject` pochodnym, jeśli używasz niektóre z opcjonalnych makra w implementacji klasy i deklaracji.

Makra pierwszego poziomu [DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic) i [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic), zezwolenie na dostęp środowiska wykonawczego do nazwy klasy i jego położenie w hierarchii. Z kolei umożliwia zrozumiałe zrzucanie diagnostycznych.

Makra drugiego poziomu [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) i [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)obejmuje wszystkie funkcje makr pierwszego poziomu i umożliwiają one obiektu "serializacji" i "archiwum".

Informacje o tworzeniu klasy pochodnej klasy Microsoft Foundation classes i klas języka C++ ogólnie rzecz biorąc i przy użyciu `CObject`, zobacz [CObject za pomocą](../../mfc/using-cobject.md) i [serializacji](../../mfc/serialization-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`CObject`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="assertvalid"></a>  CObject::AssertValid

Weryfikuje integralność tego obiektu.

```
virtual void AssertValid() const;
```

### <a name="remarks"></a>Uwagi

`AssertValid` wykonuje sprawdzanie poprawności, w tym obiekcie poprzez sprawdzenie jego stanu wewnętrznego. W wersji do debugowania biblioteki `AssertValid` może assert i dlatego zakończyć program za pomocą komunikatu zawierającego numer wiersza i nazwę pliku gdzie potwierdzenie nie powiodło się.

Podczas pisania własnych klas, należy zastąpić `AssertValid` funkcji dostarczają usługi diagnostyczne dla siebie i innych użytkowników w swojej klasy. Zastąpione `AssertValid` zwykle wywołuje `AssertValid` funkcji klasy bazowej przed sprawdzeniem elementy członkowskie danych unikatowe dla klasy pochodnej.

Ponieważ `AssertValid` jest **const** funkcji, nie masz uprawnień do zmiany stanu obiektu podczas testu. Klasy pochodne `AssertValid` funkcji nie powinna zgłaszać wyjątków, ale raczej powinny assert czy wykryją nieprawidłowy obiekt danych.

Definicja "ważność" zależy od klasy obiektu. Zgodnie z zasadą funkcja powinna sprawdzać "płytka." Oznacza to jeśli obiekt zawiera łącza do innych obiektów, należy sprawdzić aby zobaczyć, czy wskaźniki nie mają wartości null, ale nie należy wykonywać testowanie na obiekty określone przez wskaźniki ważności.

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana we wszystkich `CObject` przykłady.

[!code-cpp[NVC_MFCCObjectSample#7](../../mfc/codesnippet/cpp/cobject-class_1.cpp)]

Inny przykład, zobacz [afxdoforallobjects —](diagnostic-services.md#afxdoforallobjects).

##  <a name="cobject"></a>  CObject::CObject

Te funkcje są standardowe `CObject` konstruktorów.

```
CObject();
CObject(const CObject& objectSrc);
```

### <a name="parameters"></a>Parametry

*objectSrc*<br/>
Odwołanie do innego `CObject`

### <a name="remarks"></a>Uwagi

Domyślna wersja automatycznie jest wywoływana przez Konstruktor klasy pochodnej.

Jeśli klasa jest możliwy do serializacji (zawiera IMPLEMENT_SERIAL — makro), wówczas domyślny konstruktor (Konstruktor bez argumentów) musi mieć w swojej deklaracji klasy. Jeśli konstruktora domyślnego nie jest potrzebne, zadeklarować prywatny lub chroniony Konstruktor "pusty". Aby uzyskać więcej informacji, zobacz [CObject za pomocą](../../mfc/using-cobject.md).

Konstruktor kopiujący klasy domyślne w usłudze standard C++ wykonuje kopię przez użytkownikami. Obecność prywatna `CObject` Konstruktor kopiujący gwarantuje komunikat o błędzie kompilatora, jeśli Konstruktor kopiujący klasy jest wymagana, ale nie jest dostępna. W związku z tym należy podać konstruktora kopiującego, jeśli klasa wymaga tej możliwości.

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana w `CObject` przykłady.

[!code-cpp[NVC_MFCCObjectSample#8](../../mfc/codesnippet/cpp/cobject-class_2.cpp)]

##  <a name="dump"></a>  CObject::Dump

Zrzuty zawartości obiektu do [CDumpContext](../../mfc/reference/cdumpcontext-class.md) obiektu.

```
virtual void Dump(CDumpContext& dc) const;
```

### <a name="parameters"></a>Parametry

*Kontroler domeny*<br/>
Kontekst diagnostycznych zrzutu służąca do zrzucania zwykle `afxDump`.

### <a name="remarks"></a>Uwagi

Podczas pisania własnych klas, należy zastąpić `Dump` funkcji dostarczają usługi diagnostyczne dla siebie i innych użytkowników w swojej klasy. Zastąpione `Dump` zwykle wywołuje `Dump` funkcji klasy bazowej przed wydrukowaniem elementy członkowskie danych unikatowe dla klasy pochodnej. `CObject::Dump` Wyświetla nazwę klasy, jeśli korzysta z klasy `IMPLEMENT_DYNAMIC` lub IMPLEMENT_SERIAL — makro.

> [!NOTE]
>  Twoje `Dump` funkcji nie powinno drukować znak nowego wiersza na końcu danych wyjściowych.

`Dump` wywołania sens tylko w wersji debugowania biblioteki klas Microsoft Foundation. Należy dopasowywanie wywołania, deklaracje funkcji i implementacji funkcji za pomocą **#ifdef _DEBUG** /  `#endif` instrukcji dla kompilacji warunkowej.

Ponieważ `Dump` jest **const** funkcji, nie masz uprawnień do zmiany stanu obiektu podczas zrzutu.

[CDumpContext wstawiania (<<) — operator](../../mfc/reference/cdumpcontext-class.md#operator_lt_lt) wywołania `Dump` podczas `CObject` wskaźnik myszy zostanie wstawiona.

`Dump` zezwala na tylko "acykliczne" zrzucania obiektów. Można zrzut listy obiektów, na przykład, ale jeśli jeden z obiektów jest samej listy, zostanie ostatecznie przepełnienie stosu.

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana we wszystkich `CObject` przykłady.

[!code-cpp[NVC_MFCCObjectSample#9](../../mfc/codesnippet/cpp/cobject-class_3.cpp)]

##  <a name="getruntimeclass"></a>  CObject::GetRuntimeClass

Zwraca `CRuntimeClass` struktury odpowiadający klasy tego obiektu.

```
virtual CRuntimeClass* GetRuntimeClass() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) struktury odpowiadający tego obiektu klasy; nigdy nie **NULL**.

### <a name="remarks"></a>Uwagi

Istnieje `CRuntimeClass` dla każdego `CObject`-klasy pochodnej. Elementy członkowskie struktury są następujące:

- **LPCSTR m_lpszClassName** ciąg zakończony wartością null zawierający nazwę klasy ASCII.

- **int m_nObjectSize** rozmiar obiektu w bajtach. Jeśli obiekt ma elementy członkowskie danych prowadzące do alokacji pamięci, rozmiar pamięci nie jest dołączony.

- **UINT m_wSchema** numer schematu (-1 dla klas nonserializable). Zobacz [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) — makro opis numer schematu.

- **CObject\* (PASCAL\* m_pfnCreateObject) ()** wskaźnik funkcji do domyślnego konstruktora, który utworzył obiekt klasy (prawidłowe tylko wtedy, gdy klasa obsługuje tworzenie dynamicznej; w przeciwnym razie zwraca **o wartości NULL** ).

- **CRuntimeClass\* (PASCAL\* m_pfn_GetBaseClass) ()** aplikacja jest połączona dynamicznie AFXDLL wersję biblioteki MFC, wskaźnik do funkcji zwracającą `CRuntimeClass` strukturę klasy bazowej.

- **CRuntimeClass\* m_pBaseClass** Jeśli aplikacja jest połączone statycznie z MFC, wskaźnik do `CRuntimeClass` strukturę klasy bazowej.

Ta funkcja wymaga użycia [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic), [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate), lub [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) makra w implementacji klasy. W przeciwnym razie otrzymasz niepoprawnych wyników.

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana we wszystkich `CObject` przykłady.

[!code-cpp[NVC_MFCCObjectSample#10](../../mfc/codesnippet/cpp/cobject-class_4.cpp)]

##  <a name="iskindof"></a>  CObject::IsKindOf

Testy tego obiektu relacji do danej klasy.

```
BOOL IsKindOf(const CRuntimeClass* pClass) const;
```

### <a name="parameters"></a>Parametry

*pClass*<br/>
Wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) struktury skojarzone z Twojej `CObject`-klasy pochodnej.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli obiekt odnosi się do klasy; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja sprawdza *pClass* czy (1) jest to obiekt wybranej klasy lub (2) jest obiekt klasy pochodzącej od określonej klasy. Ta funkcja działa tylko w przypadku klasy zadeklarowane za pomocą [DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic), [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate), lub [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) makra.

Nie należy używać tej funkcji często, ponieważ unieważnia funkcja polimorfizm C++. Zamiast tego użyj funkcji wirtualnych.

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana we wszystkich `CObject` przykłady.

[!code-cpp[NVC_MFCCObjectSample#11](../../mfc/codesnippet/cpp/cobject-class_5.cpp)]

##  <a name="isserializable"></a>  CObject::IsSerializable

Sprawdza, czy ten obiekt jest uprawniona do serializacji.

```
BOOL IsSerializable() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli ten obiekt może być serializowany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Klasa może być możliwy do serializacji, jego deklaracji musi zawierać [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) makro i implementacja musi zawierać [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) makra.

> [!NOTE]
>  Nie zastępuje tej funkcji.

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana we wszystkich `CObject` przykłady.

[!code-cpp[NVC_MFCCObjectSample#12](../../mfc/codesnippet/cpp/cobject-class_6.cpp)]

##  <a name="operator_delete"></a>  Usuń CObject::operator

Dla wersji biblioteki operator **Usuń** powoduje zwolnienie pamięci przydzielonej przez operator **nowe**.

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

W wersji debugowania operatora **Usuń** uczestniczy w schemacie monitorowania alokacji, zaprojektowany do wykrywania przecieków pamięci.

Jeśli używasz wiersza kodu

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

zanim Twoje implementacji w. CPP pliku następnie trzecia wersja **Usuń** będzie używany, przechowywanie nazwy pliku i numer wiersza w zaalokowanego bloku raportowania później. Nie masz już martwić się o podanie dodatkowych parametrów; makra zajmuje się to za Ciebie.

Nawet jeśli nie używasz DEBUG_NEW w trybie debugowania, będzie nadal się pojawiać wykrywania przecieków, ale bez raportowania numer wiersza pliku źródłowego opisanych powyżej.

Jeśli zastąpisz operatory **nowe** i **Usuń**, tracą tej funkcji diagnostycznych.

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana w `CObject` przykłady.

[!code-cpp[NVC_MFCCObjectSample#15](../../mfc/codesnippet/cpp/cobject-class_8.cpp)]

##  <a name="operator_new"></a>  Nowe CObject::operator

Dla wersji biblioteki operator **nowe** wykonuje alokacji pamięci optymalne w sposób podobny do `malloc`.

```
void* PASCAL operator new(size_t nSize);
void* PASCAL operator new(size_t, void* p);

void* PASCAL operator new(
    size_t nSize,
    LPCSTR lpszFileName,
    int nLine);
```

### <a name="remarks"></a>Uwagi

W wersji debugowania operatora **nowe** uczestniczy w schemacie monitorowania alokacji, zaprojektowany do wykrywania przecieków pamięci.

Jeśli używasz wiersza kodu

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

zanim Twoje implementacji w. CPP pliku następnie drugą wersję **nowe** będzie używany, przechowywanie nazwy pliku i numer wiersza w zaalokowanego bloku raportowania później. Nie masz już martwić się o podanie dodatkowych parametrów; makra zajmuje się to za Ciebie.

Nawet jeśli nie używasz DEBUG_NEW w trybie debugowania, będzie nadal się pojawiać wykrywania przecieków, ale bez raportowania numer wiersza pliku źródłowego opisanych powyżej.

> [!NOTE]
>  Jeśli zastąpisz tego operatora, konieczne jest również przesłonięcie **Usuń**. Nie należy używać biblioteki standardowej `_new_handler` funkcji.

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana w `CObject` przykłady.

[!code-cpp[NVC_MFCCObjectSample#16](../../mfc/codesnippet/cpp/cobject-class_9.h)]

##  <a name="serialize"></a>  CObject::Serialize

Odczytuje lub zapisuje ten obiekt z lub do archiwum.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*ar*<br/>
Element `CArchive` obiektu do zserializowania do lub z.

### <a name="remarks"></a>Uwagi

Konieczne jest przesłonięcie `Serialize` dla każdej klasy, która ma być serializacji. Zastąpione `Serialize` najpierw musisz wywołać `Serialize` funkcji klasy podstawowej.

Należy również użyć [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) należy użyć makro w deklaracją klasy, a [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) makra w implementacji.

Użyj [CArchive::IsLoading](../../mfc/reference/carchive-class.md#isloading) lub [CArchive::IsStoring](../../mfc/reference/carchive-class.md#isstoring) ustalenie, czy archiwum jest ładowania lub zapisywania.

`Serialize` jest wywoływana przez [CArchive::ReadObject](../../mfc/reference/carchive-class.md#readobject) i [CArchive::WriteObject](../../mfc/reference/carchive-class.md#writeobject). Te funkcje są skojarzone z `CArchive` operator wstawiania ( **< \<**) i operatorów wyodrębniania ( **>>**).

Przykłady serializacji, zobacz artykuł [serializacja: serializacja obiektu](../../mfc/serialization-serializing-an-object.md).

### <a name="example"></a>Przykład

Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana we wszystkich `CObject` przykłady.

[!code-cpp[NVC_MFCCObjectSample#13](../../mfc/codesnippet/cpp/cobject-class_10.cpp)]

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)

