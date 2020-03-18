---
title: Usługi modelu obiektów czasu wykonywania
ms.date: 03/27/2019
helpviewer_keywords:
- run-time object model services macros
ms.assetid: 4a3e79df-2ee3-43a4-8193-20298828de85
ms.openlocfilehash: a4e471decd07cb2025b833513403b64f43105d0c
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446459"
---
# <a name="run-time-object-model-services"></a>Usługi modelu obiektów czasu wykonywania

Klasy [CObject](../../mfc/reference/cobject-class.md) i [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) hermetyzują kilka usług obiektów, w tym dostęp do informacji o klasie czasu wykonywania, serializacji i dynamicznego tworzenia obiektów. Wszystkie klasy pochodne `CObject` dziedziczą tę funkcję.

Dostęp do informacji o klasie czasu wykonywania pozwala określić informacje o klasie obiektu w czasie wykonywania. Możliwość ustalenia klasy obiektu w czasie wykonywania jest przydatna, gdy potrzebne jest dodatkowe sprawdzanie typu argumentów funkcji i gdy należy napisać kod specjalnego przeznaczenia na podstawie klasy obiektu. Informacje o klasach czasu wykonywania nie są obsługiwane bezpośrednio przez C++ język.

Serializacja jest procesem zapisywania lub odczytywania zawartości obiektu do lub z pliku. Możesz użyć serializacji do przechowywania zawartości obiektu nawet po zakończeniu działania aplikacji. Obiekt można następnie odczytać z pliku po ponownym uruchomieniu aplikacji. Takie obiekty danych są określane jako "trwałe".

Dynamiczne tworzenie obiektów umożliwia utworzenie obiektu określonej klasy w czasie wykonywania. Na przykład obiekty Document, View i Frame muszą obsługiwać tworzenie dynamiczne, ponieważ struktura musi utworzyć je dynamicznie.

Poniższa tabela zawiera listę makr MFC, które obsługują informacje o klasie czasu wykonywania, serializacji i tworzenia dynamicznego.

Aby uzyskać więcej informacji na temat tych usług obiektów i serializacji w czasie wykonywania, zobacz artykuł [CObject Class: uzyskiwanie dostępu do informacji o klasie czasu wykonywania](../../mfc/accessing-run-time-class-information.md).

### <a name="run-time-object-model-services-macros"></a>Makra usług modelu obiektów czasu wykonywania

|||
|-|-|
|[DECLARE_DYNAMIC](#declare_dynamic)|Umożliwia dostęp do informacji o klasie czasu wykonywania (należy użyć w deklaracji klasy).|
|[DECLARE_DYNCREATE](#declare_dyncreate)|Umożliwia dynamiczne tworzenie i dostęp do informacji o klasie czasu wykonywania (musi być używany w deklaracji klasy).|
|[DECLARE_SERIAL](#declare_serial)|Włącza serializację i dostęp do informacji o klasie czasu wykonywania (musi być używany w deklaracji klasy).|
|[IMPLEMENT_DYNAMIC](#implement_dynamic)|Umożliwia dostęp do informacji o klasie czasu wykonywania (należy użyć w implementacji klasy).|
|[IMPLEMENT_DYNCREATE](#implement_dyncreate)|Umożliwia dynamiczne tworzenie i dostęp do informacji w czasie wykonywania (musi być używany w implementacji klasy).|
|[IMPLEMENT_SERIAL](#implement_serial)|Zezwala na serializacji i dostęp do informacji o klasie czasu wykonywania (musi być używana w implementacji klasy).|
|[RUNTIME_CLASS](#runtime_class)|Zwraca strukturę `CRuntimeClass`, która odnosi się do nazwanej klasy.|

OLE często wymaga dynamicznego tworzenia obiektów w czasie wykonywania. Na przykład aplikacja serwera OLE musi mieć możliwość dynamicznego tworzenia elementów OLE w odpowiedzi na żądanie od klienta. Podobnie serwer automatyzacji musi mieć możliwość tworzenia elementów w odpowiedzi na żądania od klientów usługi Automation.

Biblioteka MFC zapewnia dwa makra specyficzne dla OLE.

### <a name="dynamic-creation-of-ole-objects"></a>Dynamiczne tworzenie obiektów OLE

|||
|-|-|
|[AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)|Określa, czy Biblioteka formantów wspólnych implementuje określony interfejs API.|
|[AFX_COMCTL32_IF_EXISTS2](#afx_comctl32_if_exists2)|Określa, czy Biblioteka formantów wspólnych implementuje określony interfejs API.|
|[DECLARE_OLECREATE](#declare_olecreate)|Umożliwia tworzenie obiektów za pośrednictwem automatyzacji OLE.|
|[DECLARE_OLECTLTYPE](#declare_olectltype)|Deklaruje `GetUserTypeNameID` i `GetMiscStatus` funkcje składowe klasy kontrolki.|
|[DECLARE_PROPPAGEIDS](#declare_proppageids)|Deklaruje, że formant OLE zawiera listę stron właściwości, aby wyświetlić jej właściwości.|
|[IMPLEMENT_OLECREATE](#implement_olecreate)|Umożliwia tworzenie obiektów przez system OLE.|
|[IMPLEMENT_OLECTLTYPE](#implement_olectltype)|Implementuje `GetUserTypeNameID` i `GetMiscStatus` funkcje składowe klasy kontrolki.|
|[IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags)|To makro lub [IMPLEMENT_OLECREATE](#implement_olecreate) muszą pojawić się w pliku implementacji dla każdej klasy używającej `DECLARE_OLECREATE`. |

## <a name="afx_comctl32_if_exists"></a>AFX_COMCTL32_IF_EXISTS

Określa, czy Biblioteka formantów wspólnych implementuje określony interfejs API.

### <a name="syntax"></a>Składnia

```
AFX_COMCTL32_IF_EXISTS(  proc );
```

### <a name="parameters"></a>Parametry

*złożony*<br/>
Wskaźnik na ciąg zakończony znakiem null zawierający nazwę funkcji lub określa wartość porządkową funkcji. Jeśli ten parametr jest wartością porządkową, musi być w wyrazie z małą kolejnością; słowo o wysokim porządku musi mieć wartość zero. Ten parametr musi być w formacie Unicode.

### <a name="remarks"></a>Uwagi

To makro służy do określenia, czy biblioteka wspólnych kontrolek jest funkcją określoną przez *proces* (zamiast wywoływania [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress).

### <a name="requirements"></a>Wymagania

afxcomctl32. h, afxcomctl32. inl

## <a name="afx_comctl32_if_exists2"></a>AFX_COMCTL32_IF_EXISTS2

Określa, czy Biblioteka formantów wspólnych implementuje określony interfejs API (jest to wersja Unicode [AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)).

### <a name="syntax"></a>Składnia

```
AFX_COMCTL32_IF_EXISTS2( proc );
```

### <a name="parameters"></a>Parametry

*złożony*<br/>
Wskaźnik na ciąg zakończony znakiem null zawierający nazwę funkcji lub określa wartość porządkową funkcji. Jeśli ten parametr jest wartością porządkową, musi być w wyrazie z małą kolejnością; słowo o wysokim porządku musi mieć wartość zero. Ten parametr musi być w formacie Unicode.

### <a name="remarks"></a>Uwagi

To makro służy do określenia, czy biblioteka wspólnych kontrolek jest funkcją określoną przez *proces* (zamiast wywoływania [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress). To makro jest wersją Unicode AFX_COMCTL32_IF_EXISTS.

### <a name="requirements"></a>Wymagania

afxcomctl32. h, afxcomctl32. inl

##  <a name="declare_dynamic"></a>DECLARE_DYNAMIC

Dodaje możliwość uzyskiwania dostępu do informacji w czasie wykonywania dotyczących klasy obiektu podczas wyprowadzania klasy z `CObject`.

```
DECLARE_DYNAMIC(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Rzeczywista nazwa klasy.

### <a name="remarks"></a>Uwagi

Dodaj makro DECLARE_DYNAMIC do modułu nagłówka (. h) dla klasy, a następnie Dołącz ten moduł do wszystkich modułów. cpp, które wymagają dostępu do obiektów tej klasy.

W przypadku używania makr DECLARE_ dynamicznych i IMPLEMENT_DYNAMIC zgodnie z opisem, można użyć makra RUNTIME_CLASS i funkcji `CObject::IsKindOf`, aby określić klasę obiektów w czasie wykonywania.

Jeśli DECLARE_DYNAMIC jest uwzględniona w deklaracji klasy, wówczas IMPLEMENT_DYNAMIC musi być uwzględniona w implementacji klasy.

Aby uzyskać więcej informacji dotyczących makra DECLARE_DYNAMIC, zobacz [Tematy dotyczące klasy CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [IMPLEMENT_DYNAMIC](#implement_dynamic).

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

##  <a name="declare_dyncreate"></a>DECLARE_DYNCREATE

Umożliwia dynamiczne tworzenie obiektów klas pochodnych `CObject`w czasie wykonywania.

```
DECLARE_DYNCREATE(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Rzeczywista nazwa klasy.

### <a name="remarks"></a>Uwagi

Struktura używa tej możliwości do dynamicznego tworzenia nowych obiektów. Na przykład nowy widok utworzony podczas otwierania nowego dokumentu. Klasy Document, View i Frame powinny obsługiwać tworzenie dynamiczne, ponieważ struktura musi utworzyć je dynamicznie.

Dodaj DECLARE_DYNCREATE makro w module. h dla klasy, a następnie Dołącz ten moduł do wszystkich modułów. cpp, które wymagają dostępu do obiektów tej klasy.

Jeśli DECLARE_DYNCREATE jest uwzględniona w deklaracji klasy, wówczas IMPLEMENT_DYNCREATE musi być uwzględniona w implementacji klasy.

Aby uzyskać więcej informacji dotyczących makra DECLARE_DYNCREATE, zobacz [Tematy dotyczące klasy CObject](../../mfc/using-cobject.md).

> [!NOTE]
>  Makro DECLARE_DYNCREATE zawiera wszystkie funkcje DECLARE_DYNAMIC.

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [IMPLEMENT_DYNCREATE](#implement_dyncreate).

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

## <a name="declare_olectltype"></a>DECLARE_OLECTLTYPE

Deklaruje `GetUserTypeNameID` i `GetMiscStatus` funkcje składowe klasy kontrolki.

### <a name="syntax"></a>Składnia

```
DECLARE_OLECTLTYPE( class_name )
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Nazwa klasy kontrolki.

### <a name="remarks"></a>Uwagi

`GetUserTypeNameID` i `GetMiscStatus` są czystymi funkcjami wirtualnymi zadeklarowanymi w `COleControl`. Ponieważ te funkcje są czystym wirtualnym, muszą zostać zastąpione w klasie kontrolki. Oprócz DECLARE_OLECTLTYPE należy dodać makro IMPLEMENT_OLECTLTYPE do deklaracji klasy kontrolki.

### <a name="requirements"></a>Wymagania

**Nagłówek:** 'afxctl. h

## <a name="declare_proppageids"></a>DECLARE_PROPPAGEIDS

Deklaruje, że formant OLE zawiera listę stron właściwości, aby wyświetlić jej właściwości.

### <a name="syntax"></a>Składnia

```
DECLARE_PROPPAGEIDS( class_name )
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Nazwa klasy kontrolki, która jest właścicielem stron właściwości.

### <a name="remarks"></a>Uwagi

Użyj makra `DECLARE_PROPPAGEIDS` na końcu deklaracji klasy. Następnie w pliku. cpp, który definiuje funkcje elementu członkowskiego dla klasy, użyj makra `BEGIN_PROPPAGEIDS`, wpisów makr dla każdej strony właściwości kontrolki i makra `END_PROPPAGEIDS`, aby zadeklarować koniec listy stron właściwości.

Aby uzyskać więcej informacji na temat stron właściwości, zobacz artykuł [formanty ActiveX: strony właściwości](../mfc-activex-controls-property-pages.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** 'afxctl. h

##  <a name="declare_serial"></a>DECLARE_SERIAL

Generuje kod C++ nagłówka niezbędny dla klasy pochodnej `CObject`, która może być serializowana.

```
DECLARE_SERIAL(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Rzeczywista nazwa klasy.

### <a name="remarks"></a>Uwagi

Serializacja jest procesem zapisywania lub odczytywania zawartości obiektu do i z pliku.

Użyj makra DECLARE_SERIAL w module h, a następnie Dołącz ten moduł do wszystkich modułów. cpp, które wymagają dostępu do obiektów tej klasy.

Jeśli DECLARE_SERIAL jest uwzględniona w deklaracji klasy, wówczas IMPLEMENT_SERIAL musi być uwzględniona w implementacji klasy.

Makro DECLARE_SERIAL zawiera wszystkie funkcje DECLARE_DYNAMIC i DECLARE_DYNCREATE.

Za pomocą makra AFX_API można automatycznie wyeksportować `CArchive` operator wyodrębniania dla klas, które używają makr DECLARE_SERIAL i IMPLEMENT_SERIAL. Przenawiasy w deklaracji klasy (znajdującej się w pliku h) z następującym kodem:

[!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]

Aby uzyskać więcej informacji dotyczących makra DECLARE_SERIAL, zobacz [Tematy dotyczące klasy CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCObjectSample#21](../../mfc/codesnippet/cpp/run-time-object-model-services_2.h)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

##  <a name="implement_dynamic"></a>IMPLEMENT_DYNAMIC

Generuje C++ kod niezbędny dla klasy pochodnej `CObject`dynamicznej z dostępem w czasie wykonywania do nazwy klasy i pozycji w hierarchii.

```
IMPLEMENT_DYNAMIC(class_name, base_class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Rzeczywista nazwa klasy.

*base_class_name*<br/>
Nazwa klasy bazowej.

### <a name="remarks"></a>Uwagi

Użyj makra IMPLEMENT_DYNAMIC w module. cpp, a następnie połącz otrzymany kod obiektu tylko raz.

Aby uzyskać więcej informacji, zobacz [Tematy dotyczące klas CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCObjectSample#2](../../mfc/codesnippet/cpp/run-time-object-model-services_3.h)]

[!code-cpp[NVC_MFCCObjectSample#3](../../mfc/codesnippet/cpp/run-time-object-model-services_4.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

##  <a name="implement_dyncreate"></a>IMPLEMENT_DYNCREATE

Umożliwia dynamiczne tworzenie obiektów klas pochodnych `CObject`w czasie wykonywania, gdy są używane z makrem DECLARE_DYNCREATE.

```
IMPLEMENT_DYNCREATE(class_name, base_class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Rzeczywista nazwa klasy.

*base_class_name*<br/>
Rzeczywista nazwa klasy bazowej.

### <a name="remarks"></a>Uwagi

Struktura używa tej możliwości do dynamicznego tworzenia nowych obiektów, na przykład gdy odczytuje obiekt z dysku podczas serializacji. Dodaj makro IMPLEMENT_DYNCREATE w pliku implementacji klasy. Aby uzyskać więcej informacji, zobacz [Tematy dotyczące klas CObject](../../mfc/using-cobject.md).

Jeśli używasz makr DECLARE_DYNCREATE i IMPLEMENT_DYNCREATE, możesz użyć makra RUNTIME_CLASS i funkcji elementu członkowskiego `CObject::IsKindOf`, aby określić klasę obiektów w czasie wykonywania.

Jeśli DECLARE_DYNCREATE jest uwzględniona w deklaracji klasy, wówczas IMPLEMENT_DYNCREATE musi być uwzględniona w implementacji klasy.

Należy zauważyć, że ta definicja makra wywoła domyślny konstruktor dla klasy. Jeśli Konstruktor nieuproszczony jest jawnie zaimplementowany przez klasę, musi również jawnie zaimplementować konstruktora domyślnego. Konstruktor domyślny można dodać do sekcji **prywatnych** lub **chronionych** elementów członkowskich klasy, aby zapobiec wywoływaniu go spoza implementacji klasy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCObjectSample#22](../../mfc/codesnippet/cpp/run-time-object-model-services_5.h)]

[!code-cpp[NVC_MFCCObjectSample#23](../../mfc/codesnippet/cpp/run-time-object-model-services_6.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

## <a name="implement_olecreate_flags"></a>IMPLEMENT_OLECREATE_FLAGS

To makro lub [IMPLEMENT_OLECREATE](#implement_olecreate) muszą pojawić się w pliku implementacji dla każdej klasy używającej DECLARE_OLECREATE.

### <a name="syntax"></a>Składnia

```
IMPLEMENT_OLECREATE_FLAGS( class_name, external_name, nFlags,
    l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Rzeczywista nazwa klasy.

*external_name*<br/>
Nazwa obiektu uwidaczniana innym aplikacjom (ujętym w cudzysłów).

*nFlags*<br/>
Zawiera co najmniej jedną z następujących flag:

- `afxRegInsertable` umożliwia wyświetlenie formantu w oknie dialogowym Wstaw obiekt dla obiektów OLE.
- `afxRegApartmentThreading` ustawia model wątkowości w rejestrze na ThreadingModel = Apartment.
- `afxRegFreeThreading` ustawia model wątkowości w rejestrze, aby ThreadingModel = Free.

Można połączyć dwie flagi `afxRegApartmentThreading` i `afxRegFreeThreading`, aby ustawić ThreadingModel = oba. Aby uzyskać więcej informacji na temat rejestracji modelu wątków, zobacz [InprocServer32](/windows/win32/com/inprocserver32) w Windows SDK.

*l*, *W1*, *W2*, *B1*, *B2*, *B3*, *B4*, *B5*, *B6*, *B7*, *B8* składniki klasy CLSID.

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Jeśli używasz IMPLEMENT_OLECREATE_FLAGS, możesz określić model wątkowy obsługiwany przez obiekt za pomocą parametru *nFlags* . Jeśli chcesz obsługiwać tylko jednostopniowy model, użyj IMPLEMENT_OLECREATE.

Nazwa zewnętrzna to identyfikator uwidoczniony dla innych aplikacji. Aplikacje klienckie używają nazwy zewnętrznej do żądania obiektu tej klasy z serwera automatyzacji.

Identyfikator klasy OLE jest unikatowym identyfikatorem 128-bitowym dla obiektu. Zawiera jeden **dług**, dwa **wyrazy**s i osiem **bajtów**s, reprezentowane przez *l*, *W1*, *W2*i *B1* do *B8* w opisie składni. Kreator aplikacji i kreatory kodu tworzą unikatowe identyfikatory klas OLE, zgodnie z potrzebami.

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDISP. h

## <a name="implement_olectltype"></a>IMPLEMENT_OLECTLTYPE

Implementuje `GetUserTypeNameID` i `GetMiscStatus` funkcje składowe klasy kontrolki.

### <a name="syntax"></a>Składnia

```
DECLARE_OLECTLTYPE( class_name, idsUserTypeName, dwOleMisc )
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Nazwa klasy kontrolki.

*idsUserTypeName*<br/>
Identyfikator zasobu ciągu zawierającego zewnętrzną nazwę formantu.

*dwOleMisc*<br/>
Wyliczenie zawierające co najmniej jedną flagę. Aby uzyskać więcej informacji na temat tego wyliczenia, zobacz [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) w Windows SDK.

### <a name="remarks"></a>Uwagi

Oprócz IMPLEMENT_OLECTLTYPE należy dodać makro DECLARE_OLECTLTYPE do deklaracji klasy kontrolki.

Funkcja członkowska `GetUserTypeNameID` zwraca ciąg zasobu, który identyfikuje klasę formantu. `GetMiscStatus` zwraca bity usługi OLEMISC dla kontrolki. To wyliczenie Określa kolekcję ustawień opisujących różne cechy kontrolki. Pełny opis ustawień OLEMISC można znaleźć w sekcji [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) w Windows SDK.

> [!NOTE]
>  Domyślne ustawienia używane przez ControlWizard ActiveX to: OLEMISC_ACTIVATEWHENVISIBLE, OLEMISC_SETCLIENTSITEFIRST, OLEMISC_INSIDEOUT, OLEMISC_CANTLINKINSIDE i OLEMISC_RECOMPOSEONRESIZE.

### <a name="requirements"></a>Wymagania

**Nagłówek:** 'afxctl. h

##  <a name="implement_serial"></a>IMPLEMENT_SERIAL

Generuje C++ kod niezbędny dla klasy pochodnej `CObject`dynamicznej z dostępem w czasie wykonywania do nazwy klasy i pozycji w hierarchii.

```
IMPLEMENT_SERIAL(class_name, base_class_name, wSchema)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Rzeczywista nazwa klasy.

*base_class_name*<br/>
Nazwa klasy bazowej.

*wSchema*<br/>
UINT "numer wersji", który zostanie zakodowany w archiwum, aby umożliwić deserializacji program do identyfikowania i obsługi danych utworzonych przez wcześniejsze wersje programu. Numer schematu klasy nie może mieć wartości-1.

### <a name="remarks"></a>Uwagi

Użyj makra IMPLEMENT_SERIAL w module. cpp; następnie połącz otrzymany kod obiektu tylko raz.

Za pomocą makra AFX_API można automatycznie wyeksportować `CArchive` operator wyodrębniania dla klas, które używają makr DECLARE_SERIAL i IMPLEMENT_SERIAL. Przenawiasy w deklaracji klasy (znajdującej się w pliku h) z następującym kodem:

[!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]

Aby uzyskać więcej informacji, zobacz [Tematy dotyczące klas CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCObjectSample#24](../../mfc/codesnippet/cpp/run-time-object-model-services_7.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

##  <a name="runtime_class"></a>RUNTIME_CLASS

Pobiera strukturę klasy czasu wykonywania z nazwy C++ klasy.

```
RUNTIME_CLASS(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Rzeczywista nazwa klasy (nieujęta w cudzysłów).

### <a name="remarks"></a>Uwagi

RUNTIME_CLASS zwraca wskaźnik do struktury [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) dla klasy określonej przez *class_name*. Tylko klasy pochodne `CObject`zadeklarowane za pomocą DECLARE_DYNAMIC, DECLARE_DYNCREATE lub DECLARE_SERIAL będą zwracać wskaźniki do struktury `CRuntimeClass`.

Aby uzyskać więcej informacji, zobacz [Tematy dotyczące klas CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCObjectSample#25](../../mfc/codesnippet/cpp/run-time-object-model-services_8.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** AFX. h

##  <a name="declare_olecreate"></a>DECLARE_OLECREATE

Umożliwia tworzenie obiektów klas pochodnych opartych na `CCmdTarget`za pośrednictwem automatyzacji OLE.

```
DECLARE_OLECREATE(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Rzeczywista nazwa klasy.

### <a name="remarks"></a>Uwagi

To makro umożliwia innym aplikacjom obsługującym technologię OLE Tworzenie obiektów tego typu.

Dodaj DECLARE_OLECREATE makro w module. h dla klasy, a następnie Dołącz ten moduł do wszystkich modułów. cpp, które wymagają dostępu do obiektów tej klasy.

Jeśli DECLARE_OLECREATE jest uwzględniona w deklaracji klasy, wówczas IMPLEMENT_OLECREATE musi być uwzględniona w implementacji klasy. Deklaracja klasy używająca DECLARE_OLECREATE musi również używać DECLARE_DYNCREATE lub DECLARE_SERIAL.

### <a name="requirements"></a>Wymagania

**Nagłówek**: AFXDISP. h

##  <a name="implement_olecreate"></a>IMPLEMENT_OLECREATE

To makro lub [IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags) muszą pojawić się w pliku implementacji dla każdej klasy używającej `DECLARE_OLECREATE`.

```
IMPLEMENT_OLECREATE(class_name, external_name, l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Rzeczywista nazwa klasy.

*external_name*<br/>
Nazwa obiektu uwidaczniana innym aplikacjom (ujętym w cudzysłów).

*l*, *W1*, *W2*, *B1*, *B2*, *B3*, *B4*, *B5*, *B6*, *B7*, *B8* składniki klasy CLSID.

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Jeśli używasz IMPLEMENT_OLECREATE, domyślnie jest obsługiwany tylko jeden model wątkowości. Jeśli używasz IMPLEMENT_OLECREATE_FLAGS, możesz określić model wątkowy obsługiwany przez obiekt za pomocą parametru *nFlags* .

Nazwa zewnętrzna to identyfikator uwidoczniony dla innych aplikacji. Aplikacje klienckie używają nazwy zewnętrznej do żądania obiektu tej klasy z serwera automatyzacji.

Identyfikator klasy OLE jest unikatowym identyfikatorem 128-bitowym dla obiektu. Zawiera jeden **dług**, dwa **wyrazy**s i osiem **bajtów**s, reprezentowane przez *l*, *W1*, *W2*i *B1* do *B8* w opisie składni. Kreator aplikacji i kreatory kodu tworzą unikatowe identyfikatory klas OLE, zgodnie z potrzebami.

### <a name="requirements"></a>Wymagania

**Nagłówek**: AFXDISP. h

## <a name="see-also"></a>Zobacz też

[Makra i Globals](mfc-macros-and-globals.md)<br/>
[Izolacja biblioteki formantów wspólnych MFC](../isolation-of-the-mfc-common-controls-library.md)<br/>
[Klucz CLSID](/windows/win32/com/clsid-key-hklm)
