---
title: CObject — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CObject [MFC], CObject
- CObject [MFC], AssertValid
- CObject [MFC], Dump
- CObject [MFC], GetRuntimeClass
- CObject [MFC], IsKindOf
- CObject [MFC], IsSerializable
- CObject [MFC], Serialize
ms.assetid: 95e9acd3-d9eb-4ac0-b52b-ca4a501a7a3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 34babea47abaab9fcfb45f57aedd5cec94e82963
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37041714"
---
# <a name="cobject-class"></a>CObject — klasa
Główna klasa podstawowa dla Microsoft Foundation Class Library.  
  
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
|[CObject::Dump](#dump)|Tworzy zrzut diagnostycznych tego obiektu.|  
|[CObject::GetRuntimeClass](#getruntimeclass)|Zwraca `CRuntimeClass` struktury odpowiadający klasa ten obiekt.|  
|[CObject::IsKindOf](#iskindof)|Testy relacji tego obiektu do danej klasy.|  
|[CObject::IsSerializable](#isserializable)|Testy, aby sprawdzić, czy ten obiekt może być Zserializowany.|  
|[CObject::Serialize](#serialize)|Ładuje lub przechowuje obiekt z/do archiwum.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[Usuń CObject::operator](#operator_delete)|Specjalne **usunąć** operatora.|  
|[Nowe CObject::operator](#operator_new)|Specjalne **nowe** operatora.|  
  
## <a name="remarks"></a>Uwagi  
 Służy on jako katalog główny nie tylko dla biblioteki klas takich jak `CFile` i `CObList`, ale także dla klasy, które można zapisać. `CObject` udostępnia podstawowe usługi, w tym  
  
-   Obsługa serializacji  
  
-   Informacje o klasie czasu wykonywania  
  
-   Dane wyjściowe diagnostyki obiektu  
  
-   Zgodność z klasy kolekcji  
  
 Należy pamiętać, że `CObject` nie obsługuje wielu dziedziczenia. Z klas pochodnych może mieć tylko jeden `CObject` klasy podstawowej, a `CObject` musi być lewej w hierarchii. Jest dozwolone, jednak mieć struktury i nie- `CObject`-pochodnych klas w gałęzi dziedziczenia wielokrotnego po prawej stronie.  
  
 Zostanie osiągnięcia najważniejszych korzyści z `CObject` pochodnym, jeśli używasz niektóre opcjonalne makra w implementacji klasy i deklaracje.  
  
 Makra pierwszego stopnia [declare_dynamic —](run-time-object-model-services.md#declare_dynamic) i [implement_dynamic —](run-time-object-model-services.md#implement_dynamic), zezwalają na dostęp do środowiska wykonawczego na nazwę klasy i jej położenie w hierarchii. Z kolei umożliwia łatwy do rozpoznania zrzucanie diagnostycznych.  
  
 Makra drugiego poziomu [declare_serial —](run-time-object-model-services.md#declare_serial) i [implement_serial —](run-time-object-model-services.md#implement_serial), obejmują wszystkie funkcje makr pierwszego stopnia, i umożliwiają obiektu "serializacji" do i z "archiwum".  
  
 Informacje dotyczące tworzenia klasy pochodnej klasy C++ i Microsoft Foundation classes ogólnie i przy użyciu `CObject`, zobacz [CObject za pomocą](../../mfc/using-cobject.md) i [serializacji](../../mfc/serialization-in-mfc.md).  
  
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
 `AssertValid` wykonuje sprawdzanie poprawności, w tym obiekcie poprzez sprawdzenie jego stanu wewnętrznego. W wersji do debugowania biblioteki `AssertValid` może assert i w związku z tym zakończyć program komunikat zawierający listę numeru wiersza i nazwa pliku których potwierdzenia nie powiodło się.  
  
 Podczas pisania własne klasy powinny zastępować `AssertValid` funkcji usługi diagnostyczne dla siebie i innych użytkowników klasy. Zastąpione `AssertValid` zwykle wymaga `AssertValid` funkcja jej klasa podstawowa przed zaewidencjonowaniem elementy członkowskie danych unikatowe dla klasy pochodnej.  
  
 Ponieważ `AssertValid` jest **const** funkcji, nie masz uprawnień do zmiany stanu obiektu podczas testu. Klasy pochodne `AssertValid` funkcji nie powinny zgłaszać wyjątków, ale raczej powinny assert czy wykryją obiektu nieprawidłowe dane.  
  
 Definicja "ważności" zależy od klasy obiektu. Zgodnie z zasadą funkcji należy sprawdzić "skrócona." Oznacza to jeśli obiekt zawiera łącza do innych obiektów, należy sprawdzić aby zobaczyć, czy wskaźniki nie mają wartości null, ale nie należy przeprowadzać testowania na obiekty określone przez wskaźniki ważności.  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana we wszystkich `CObject` przykłady.  
  
 [!code-cpp[NVC_MFCCObjectSample#7](../../mfc/codesnippet/cpp/cobject-class_1.cpp)]  
  
 Na przykład innego, zobacz [afxdoforallobjects —](diagnostic-services.md#afxdoforallobjects).  
  
##  <a name="cobject"></a>  CObject::CObject  
 Te funkcje są standardowe `CObject` konstruktorów.  
  
```  
CObject();  
CObject(const CObject& objectSrc);
```  
  
### <a name="parameters"></a>Parametry  
 *objectSrc*  
 Odwołanie do innego `CObject`  
  
### <a name="remarks"></a>Uwagi  
 Domyślna wersja jest wywoływana automatycznie przez konstruktora klasy pochodnej.  
  
 Jeśli klasa jest możliwy do serializacji (zawiera implement_serial — makro), wówczas musi mieć konstruktora domyślnego (konstruktora bez argumentów) w Twojej deklaracji klasy. Jeśli konstruktora domyślnego nie jest wymagane, Zadeklaruj prywatnej lub chronione "pustego" konstruktora. Aby uzyskać więcej informacji, zobacz [CObject za pomocą](../../mfc/using-cobject.md).  
  
 Konstruktor kopiujący klasy domyślne w usłudze standard C++ powoduje przywrócenie kopii elementu członkowskiego elementu członkowskiego. Obecność prywatna `CObject` Konstruktor kopiujący gwarantuje komunikat o błędzie kompilatora, jeśli Konstruktor kopiujący klasy jest wymagana, ale nie jest dostępna. W związku z tym musisz podać konstruktora kopiującego, jeśli klasa ta funkcja jest wymagana.  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana w `CObject` przykłady.  
  
 [!code-cpp[NVC_MFCCObjectSample#8](../../mfc/codesnippet/cpp/cobject-class_2.cpp)]  
  
##  <a name="dump"></a>  CObject::Dump  
 Zrzuty zawartości obiektu do [CDumpContext](../../mfc/reference/cdumpcontext-class.md) obiektu.  
  
```  
virtual void Dump(CDumpContext& dc) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *Kontroler domeny*  
 Zrzucanie, zwykle w kontekście diagnostycznych zrzutu `afxDump`.  
  
### <a name="remarks"></a>Uwagi  
 Podczas pisania własne klasy powinny zastępować `Dump` funkcji usługi diagnostyczne dla siebie i innych użytkowników klasy. Zastąpione `Dump` zwykle wymaga `Dump` funkcja jej klasa podstawowa przed wydrukowaniem elementy członkowskie danych unikatowe dla klasy pochodnej. `CObject::Dump` Wyświetla nazwę klasy, jeśli używa klasy `IMPLEMENT_DYNAMIC` lub implement_serial — makro.  
  
> [!NOTE]
>  Twoje `Dump` funkcja powinna nie do drukowania znaku nowego wiersza na koniec dane wyjściowe.  
  
 `Dump` wywołania sensu tylko w wersji do debugowania programu Microsoft Foundation Class Library. Należy nawiasów wywołania, deklaracje funkcji i funkcji implementacje z **#ifdef _DEBUG** /  `#endif` instrukcje dla kompilacji warunkowej.  
  
 Ponieważ `Dump` jest **const** funkcji, nie masz uprawnień do zmiany stanu obiektu podczas zrzutu.  
  
 [CDumpContext wstawiania (<<) — operator](../../mfc/reference/cdumpcontext-class.md#operator_lt_lt) wywołania `Dump` podczas `CObject` dodaje się wskaźnika.  
  
 `Dump` zezwala na tylko "acykliczne" zrzucanie obiektów. Można zrzut listy obiektów, na przykład, ale jeśli jest jednym z obiektów samej listy, zostanie ostatecznie przepełnienie stosu.  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana we wszystkich `CObject` przykłady.  
  
 [!code-cpp[NVC_MFCCObjectSample#9](../../mfc/codesnippet/cpp/cobject-class_3.cpp)]  
  
##  <a name="getruntimeclass"></a>  CObject::GetRuntimeClass  
 Zwraca `CRuntimeClass` struktury odpowiadający klasa ten obiekt.  
  
```  
virtual CRuntimeClass* GetRuntimeClass() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) struktury odpowiadający klasa ten obiekt; nigdy nie **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Istnieje `CRuntimeClass` struktury dla każdego `CObject`-klasy. Elementy członkowskie struktury są następujące:  
  
- **LPCSTR m_lpszClassName** zerem ciąg zawierający nazwę klasy zestawu ASCII.  
  
- **int m_nObjectSize** rozmiar obiektu, w bajtach. Jeśli obiekt ma elementy członkowskie danych prowadzące do alokacji pamięci, rozmiar pamięci nie jest dołączony.  
  
- **UINT m_wSchema** numer schematu (-1 dla klas nonserializable). Zobacz [implement_serial —](run-time-object-model-services.md#implement_serial) makro opis numer schematu.  
  
- **CObject\* (PASCAL\* m_pfnCreateObject) ()** wskaźnik funkcji do domyślnego konstruktora, który utworzył obiekt klasy (prawidłowe tylko wtedy, gdy klasa obsługuje tworzenie dynamicznej; w przeciwnym razie zwraca **wartości NULL** ).  
  
- **CRuntimeClass\* (PASCAL\* m_pfn_GetBaseClass) ()** aplikacji jest połączona dynamicznie do wersja AFXDLL MFC, wskaźnika do funkcji zwracającą `CRuntimeClass` struktury klasy podstawowej.  
  
- **CRuntimeClass\* m_pBaseClass** Jeśli aplikacja jest połączone statycznie z MFC, wskaźnik do `CRuntimeClass` struktury klasy podstawowej.  
  
 Ta funkcja wymaga użycia [implement_dynamic —](run-time-object-model-services.md#implement_dynamic), [implement_dyncreate —](run-time-object-model-services.md#implement_dyncreate), lub [implement_serial —](run-time-object-model-services.md#implement_serial) makra w implementacji klasy. W przeciwnym razie otrzymasz niepoprawnych wyników.  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana we wszystkich `CObject` przykłady.  
  
 [!code-cpp[NVC_MFCCObjectSample#10](../../mfc/codesnippet/cpp/cobject-class_4.cpp)]  
  
##  <a name="iskindof"></a>  CObject::IsKindOf  
 Testy relacji tego obiektu do danej klasy.  
  
```  
BOOL IsKindOf(const CRuntimeClass* pClass) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *pClass*  
 Wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) struktury skojarzone z Twojej `CObject`-klasy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli obiekt odpowiada klasie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja sprawdza *pClass* czy (1) jest obiekt określonej klasy lub (2) jest obiekt klasy pochodzącej od określonej klasy. Ta funkcja działa tylko w przypadku klasy zadeklarowany z [declare_dynamic —](run-time-object-model-services.md#declare_dynamic), [declare_dyncreate —](run-time-object-model-services.md#declare_dyncreate), lub [declare_serial —](run-time-object-model-services.md#declare_serial) makra.  
  
 Należy używać tej funkcji często, ponieważ jego pozbawia funkcji polimorfizm C++. Zamiast tego użyj funkcji wirtualnych.  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana we wszystkich `CObject` przykłady.  
  
 [!code-cpp[NVC_MFCCObjectSample#11](../../mfc/codesnippet/cpp/cobject-class_5.cpp)]  
  
##  <a name="isserializable"></a>  CObject::IsSerializable  
 Sprawdza, czy ten obiekt nie kwalifikuje się do serializacji.  
  
```  
BOOL IsSerializable() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli ten obiekt może być Zserializowany; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Dla klasy jako możliwy do serializacji, jego deklaracji musi zawierać [declare_serial —](run-time-object-model-services.md#declare_serial) makro i wykonania musi zawierać [implement_serial —](run-time-object-model-services.md#implement_serial) makra.  
  
> [!NOTE]
>  Nie zastępuj tej funkcji.  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana we wszystkich `CObject` przykłady.  
  
 [!code-cpp[NVC_MFCCObjectSample#12](../../mfc/codesnippet/cpp/cobject-class_6.cpp)]  
  
##  <a name="operator_delete"></a>  Usuń CObject::operator  
 Dla wersji biblioteki operator **usunąć** zwalnia pamięć przydzielona przez operatora **nowe**.  
  
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
 W wersji do debugowania operator **usunąć** uczestniczy w schemacie monitorowania alokacji umożliwiającą wykrywanie przecieków pamięci.  
  
 Jeśli używasz wiersza kodu  
  
 [!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]  
  
 przed każdą z implementacji w. CPP pliku następnie trzeciej wersji aplikacji **usunąć** będzie używany, przechowywanie filename i numer wiersza w bloku przydzielone później raportowania. Nie trzeba martwić się o podanie dodatkowych parametrów; makra odpowiada on za który dla Ciebie.  
  
 Nawet jeśli nie używasz `DEBUG_NEW` w trybie debugowania, nadal otrzymywać wykrywanie przecieków, ale bez raportowania numer wiersza pliku źródłowego opisane powyżej.  
  
 Jeśli przesłonić operatory **nowe** i **usunąć**, stracisz tej możliwości diagnostycznych.  
  
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
 W wersji do debugowania operator **nowe** uczestniczy w schemacie monitorowania alokacji umożliwiającą wykrywanie przecieków pamięci.  
  
 Jeśli używasz wiersza kodu  
  
 [!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]  
  
 przed każdą z implementacji w. CPP pliku następnie druga wersja **nowe** będzie używany, przechowywanie filename i numer wiersza w bloku przydzielone później raportowania. Nie trzeba martwić się o podanie dodatkowych parametrów; makra odpowiada on za który dla Ciebie.  
  
 Nawet jeśli nie używasz `DEBUG_NEW` w trybie debugowania, nadal otrzymywać wykrywanie przecieków, ale bez raportowania numer wiersza pliku źródłowego opisane powyżej.  
  
> [!NOTE]
>  Jeśli zastąpienie tego operatora, należy również zmienić **usunąć**. Nie używaj biblioteki standardowej **_new_handler** funkcji.  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana w `CObject` przykłady.  
  
 [!code-cpp[NVC_MFCCObjectSample#16](../../mfc/codesnippet/cpp/cobject-class_9.h)]  
  
##  <a name="serialize"></a>  CObject::Serialize  
 Odczytuje i zapisuje ten obiekt z lub do archiwum.  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parametry  
 *ar*  
 A `CArchive` obiektu do zserializowania do lub z.  
  
### <a name="remarks"></a>Uwagi  
 Konieczne jest przesłonięcie `Serialize` dla każdej klasy, która ma być serializacji. Zastąpione `Serialize` najpierw musisz wywołać `Serialize` funkcji klasy podstawowej.  
  
 Należy również użyć [declare_serial —](run-time-object-model-services.md#declare_serial) należy użyć makra w Twojej deklaracji klasy, a [implement_serial —](run-time-object-model-services.md#implement_serial) makra w implementacji.  
  
 Użyj [CArchive::IsLoading](../../mfc/reference/carchive-class.md#isloading) lub [CArchive::IsStoring](../../mfc/reference/carchive-class.md#isstoring) ustalenie, czy archiwum jest ładowania lub przechowywania.  
  
 `Serialize` Metoda jest wywoływana przez [CArchive::ReadObject](../../mfc/reference/carchive-class.md#readobject) i [CArchive::WriteObject](../../mfc/reference/carchive-class.md#writeobject). Te funkcje są skojarzone z `CArchive` operatora wstawiania ( **< \<**) i operatorów wyodrębniania ( **>>**).  
  
 Przykłady serializacji, zobacz artykuł [serializacja: serializacja obiektu](../../mfc/serialization-serializing-an-object.md).  
  
### <a name="example"></a>Przykład  
 Zobacz [CObList::CObList](../../mfc/reference/coblist-class.md#coblist) listę `CAge` klasa używana we wszystkich `CObject` przykłady.  
  
 [!code-cpp[NVC_MFCCObjectSample#13](../../mfc/codesnippet/cpp/cobject-class_10.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



