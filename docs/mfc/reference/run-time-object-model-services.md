---
title: Usługi modelu obiektów czasu wykonywania
ms.date: 03/27/2019
helpviewer_keywords:
- run-time object model services macros
ms.assetid: 4a3e79df-2ee3-43a4-8193-20298828de85
ms.openlocfilehash: 5ea7900df8d71157a7ea77dd27a8ba83dfe259a1
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611750"
---
# <a name="run-time-object-model-services"></a>Usługi modelu obiektów czasu wykonywania

Klasy [CObject](../../mfc/reference/cobject-class.md) i [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) hermetyzacji kilka usług obiekt, w tym dostęp do informacji o klasie czasu wykonywania serializacji i dynamiczne tworzenie obiektów. Wszystkie klasy pochodne `CObject` dziedziczą tę funkcję.

Dostęp do informacji o klasie czasu wykonywania umożliwia określenie informacji na temat klasy obiektu w czasie wykonywania. Możliwość określenia klasy obiektu w czasie wykonywania jest przydatne, gdy będą potrzebne dodatkowe sprawdzania typów argumentów funkcji i kiedy należy napisać kod specjalnych, na podstawie klasy obiektu. Informacje o klasie czasu wykonywania nie jest obsługiwana bezpośrednio za pomocą języka C++.

Serializacja jest proces wpisywanie lub odczytywanie zawartości obiektu do lub z pliku. Serializacja służy do przechowywania zawartości obiektu, nawet po zakończeniu aplikacja. Obiekt można odczytywać z pliku po ponownym uruchomieniu aplikacji. Takie obiekty danych są określane jako "stałe".

Dynamiczne tworzenie obiektów umożliwia utworzenie obiektu klasy określonej w czasie wykonywania. Na przykład dokument, widoku i ramki obiektów musi obsługiwać dynamiczne tworzenie ponieważ struktura należy utworzyć je dynamicznie.

W poniższej tabeli wymieniono makr MFC, które obsługuje informacje o klasie czasu wykonywania serializacji i dynamiczne tworzenie.

Aby uzyskać więcej informacji na temat tych obiektów czasu wykonywania usług i serializacji, zobacz artykuł [klasa CObject: Uzyskiwanie dostępu do informacji o klasie czasu wykonywania](../../mfc/accessing-run-time-class-information.md).

### <a name="run-time-object-model-services-macros"></a>Makra usługi modelu obiektów czasu wykonywania

|||
|-|-|
|[DECLARE_DYNAMIC](#declare_dynamic)|Umożliwia dostęp do informacji o klasie czasu wykonywania (muszą być używane w deklaracji klasy).|
|[DECLARE_DYNCREATE](#declare_dyncreate)|Umożliwia dynamiczne tworzenie i dostęp do informacji o klasie czasu wykonywania (muszą być używane w deklaracji klasy).|
|[DECLARE_SERIAL](#declare_serial)|Umożliwia serializacji i dostęp do informacji o klasie czasu wykonywania (muszą być używane w deklaracji klasy).|
|[IMPLEMENT_DYNAMIC](#implement_dynamic)|Umożliwia dostęp do informacji o klasie czasu wykonywania (muszą być używane w implementacji klasy).|
|[IMPLEMENT_DYNCREATE](#implement_dyncreate)|Umożliwia dynamiczne tworzenie i dostęp do informacji o czasie wykonywania (muszą być używane w implementacji klasy).|
|[IMPLEMENT_SERIAL](#implement_serial)|Zezwala na serializacji i dostęp do informacji o klasie czasu wykonywania (muszą być używane w implementacji klasy).|
|[RUNTIME_CLASS](#runtime_class)|Zwraca `CRuntimeClass` strukturę, która odnosi się do nazwanej klasie.|

OLE wymaga często dynamiczne tworzenie obiektów w czasie wykonywania. Aplikacja serwera OLE musi być na przykład, możesz tworzyć elementy OLE dynamicznie w odpowiedzi na żądanie od klienta. Podobnie serwer automatyzacji musi mieć możliwość tworzenia elementów w odpowiedzi na żądania od klientów automatyzacji.

Bibliotekę Microsoft Foundation Class zapewnia dwa makra określonych OLE.

### <a name="dynamic-creation-of-ole-objects"></a>Dynamiczne tworzenie obiektów OLE

|||
|-|-|
|[AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)|Określa, czy biblioteki formantów wspólnych implementuje określony interfejs API.|
|[AFX_COMCTL32_IF_EXISTS2](#afx_comctl32_if_exists2)|Określa, czy biblioteki formantów wspólnych implementuje określony interfejs API.|
|[DECLARE_OLECREATE](#declare_olecreate)|Umożliwia obiektów można utworzyć za pomocą automatyzacji OLE.|
|[DECLARE_OLECTLTYPE](#declare_olectltype)|Deklaruje `GetUserTypeNameID` i `GetMiscStatus` funkcji składowych klasy kontrolki.|
|[DECLARE_PROPPAGEIDS](#declare_proppageids)|Deklaruje, że formant OLE zawiera listę stron właściwości, aby wyświetlić jego właściwości.|
|[IMPLEMENT_OLECREATE](#implement_olecreate)|Umożliwia obiekty, które ma zostać utworzony przez OLE system.|
|[IMPLEMENT_OLECTLTYPE](#implement_olectltype)|Implementuje `GetUserTypeNameID` i `GetMiscStatus` funkcji składowych klasy kontrolki.|
|[IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags)|Albo to makro lub [IMPLEMENT_OLECREATE](#implement_olecreate) musi znajdować się w pliku implementacji dla każdej klasy, która używa `DECLARE_OLECREATE`. |

## <a name="afx_comctl32_if_exists"></a> AFX_COMCTL32_IF_EXISTS

Określa, czy biblioteki formantów wspólnych implementuje określony interfejs API.

### <a name="syntax"></a>Składnia

  ```
AFX_COMCTL32_IF_EXISTS(  proc );
```

### <a name="parameters"></a>Parametry

*Procedura*<br/>
Wskaźnik na ciąg zakończony wartością null zawierający nazwę funkcji, lub określa wartość porządkową przez funkcję. Jeśli ten parametr ma wartość będącą liczbą porządkową, musi być w programie word niskiego rzędu; word wyższego rzędu musi mieć wartość zero. Ten parametr musi być w formacie Unicode.

### <a name="remarks"></a>Uwagi

Użyj tego makra, aby określić, czy biblioteki formantów wspólnych funkcji określił *proc* (zamiast wywoływać metodę [GetProcAddress](/windows/desktop/api/libloaderapi/nf-libloaderapi-getprocaddress).

### <a name="requirements"></a>Wymagania

afxcomctl32.h, afxcomctl32.inl

## <a name="afx_comctl32_if_exists2"></a>  AFX_COMCTL32_IF_EXISTS2

Określa, czy biblioteki formantów wspólnych implementuje określony interfejs API (to jest wersja Unicode [AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)).

### <a name="syntax"></a>Składnia

```
AFX_COMCTL32_IF_EXISTS2( proc );
```

### <a name="parameters"></a>Parametry

*Procedura*<br/>
Wskaźnik na ciąg zakończony wartością null zawierający nazwę funkcji, lub określa wartość porządkową przez funkcję. Jeśli ten parametr ma wartość będącą liczbą porządkową, musi być w programie word niskiego rzędu; word wyższego rzędu musi mieć wartość zero. Ten parametr musi być w formacie Unicode.

### <a name="remarks"></a>Uwagi

Użyj tego makra, aby określić, czy biblioteki formantów wspólnych funkcji określił *proc* (zamiast wywoływać metodę [GetProcAddress](/windows/desktop/api/libloaderapi/nf-libloaderapi-getprocaddress). To makro jest wersją Unicode AFX_COMCTL32_IF_EXISTS.

### <a name="requirements"></a>Wymagania

afxcomctl32.h, afxcomctl32.inl

##  <a name="declare_dynamic"></a>  DECLARE_DYNAMIC

Dodaje możliwość dostępu do środowiska wykonawczego o klasę obiektu podczas wyprowadzania z klasy `CObject`.

```
DECLARE_DYNAMIC(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Rzeczywista nazwa klasy.

### <a name="remarks"></a>Uwagi

Dodaj DECLARE_DYNAMIC — makro modułu nagłówków (.h) dla klasy, a następnie dołączyć ten moduł we wszystkich modułach .cpp, którzy potrzebują dostępu do obiektów tej klasy.

Jeśli używasz DECLARE_ dynamiczne i IMPLEMENT_DYNAMIC makra, zgodnie z opisem, następnie można użyć makra RUNTIME_CLASS i `CObject::IsKindOf` funkcję, aby określić klasę obiektów w czasie wykonywania.

Jeśli DECLARE_DYNAMIC jest uwzględniona w deklaracji klasy, IMPLEMENT_DYNAMIC muszą być zawarte w implementacji klasy.

Aby uzyskać więcej informacji na temat DECLARE_DYNAMIC — makro, zobacz [tematy klasa CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Przykład

Zobacz przykład [IMPLEMENT_DYNAMIC](#implement_dynamic).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="declare_dyncreate"></a>  DECLARE_DYNCREATE

Włącza obiektów `CObject`-pochodne klasy można tworzyć dynamicznie w czasie wykonywania.

```
DECLARE_DYNCREATE(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Rzeczywista nazwa klasy.

### <a name="remarks"></a>Uwagi

Środowisko wykorzystuje tę możliwość do dynamicznego tworzenia nowych obiektów. Na przykład nowy widok utworzony po otwarciu nowego dokumentu. Klasy ramki dokumentów i wyświetlanie powinien obsługiwać dynamiczne tworzenie, ponieważ struktura należy utworzyć je dynamicznie.

Dodaj DECLARE_DYNCREATE — makro w module .h klasy, a następnie dołączyć ten moduł we wszystkich modułach .cpp, którzy potrzebują dostępu do obiektów tej klasy.

Jeśli DECLARE_DYNCREATE jest uwzględniona w deklaracji klasy, IMPLEMENT_DYNCREATE muszą być zawarte w implementacji klasy.

Aby uzyskać więcej informacji na temat DECLARE_DYNCREATE — makro, zobacz [tematy klasa CObject](../../mfc/using-cobject.md).

> [!NOTE]
>  DECLARE_DYNCREATE — makro obejmuje wszystkie funkcje programu DECLARE_DYNAMIC.

### <a name="example"></a>Przykład

Zobacz przykład [IMPLEMENT_DYNCREATE](#implement_dyncreate).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="declareolectltype"></a>DECLARE_OLECTLTYPE

Deklaruje `GetUserTypeNameID` i `GetMiscStatus` funkcji składowych klasy kontrolki.

### <a name="syntax"></a>Składnia

```
DECLARE_OLECTLTYPE( class_name )
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Nazwa klasy kontrolki.

### <a name="remarks"></a>Uwagi

`GetUserTypeNameID` i `GetMiscStatus` czystych funkcji wirtualnych zadeklarowanych w `COleControl`. Ponieważ te funkcje są czyste wirtualnych, ich musi zostać zastąpiona w klasie kontrolki. Oprócz DECLARE_OLECTLTYPE należy dodać IMPLEMENT_OLECTLTYPE — makro do sterowania deklaracją klasy.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxctl.h

## <a name="declareproppageids"></a>DECLARE_PROPPAGEIDS

Deklaruje, że formant OLE zawiera listę stron właściwości, aby wyświetlić jego właściwości.

### <a name="syntax"></a>Składnia

```
DECLARE_PROPPAGEIDS( class_name )
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Nazwa klasy kontrolki, która jest właścicielem strony właściwości.

### <a name="remarks"></a>Uwagi

Użyj `DECLARE_PROPPAGEIDS` — makro na końcu deklaracją klasy. Następnie w pliku .cpp, który definiuje funkcji elementów członkowskich klasy, należy użyć `BEGIN_PROPPAGEIDS` makr, makro wpisy dla każdej strony właściwości formantu, a `END_PROPPAGEIDS` makra, aby zadeklarować na końcu listy strony właściwości.

Aby uzyskać więcej informacji na stronach właściwości, zobacz artykuł [kontrolek ActiveX: Strony właściwości](../mfc-activex-controls-property-pages.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxctl.h

##  <a name="declare_serial"></a>  DECLARE_SERIAL

Generuje kod nagłówka C++ niezbędnych do `CObject`-klasy, który może być serializowany.

```
DECLARE_SERIAL(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Rzeczywista nazwa klasy.

### <a name="remarks"></a>Uwagi

Serializacja jest proces wpisywanie lub odczytywanie zawartości obiektu do i z pliku.

Użyj DECLARE_SERIAL — makro w module .h, a następnie dołącz ten moduł we wszystkich modułach .cpp, którzy potrzebują dostępu do obiektów tej klasy.

Jeśli DECLARE_SERIAL jest uwzględniona w deklaracji klasy, IMPLEMENT_SERIAL muszą być zawarte w implementacji klasy.

DECLARE_SERIAL — makro obejmuje wszystkie funkcje DECLARE_DYNAMIC i DECLARE_DYNCREATE.

Aby wyeksportować automatycznie, można użyć makra AFX_API `CArchive` operator wyodrębniania dla klas, które używają DECLARE_SERIAL i IMPLEMENT_SERIAL makr. Dopasowywanie deklaracji klasy (znajdujący się w pliku .h) z następującym kodem:

[!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]

Aby uzyskać więcej informacji na temat DECLARE_SERIAL — makro, zobacz [tematy klasa CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCObjectSample#21](../../mfc/codesnippet/cpp/run-time-object-model-services_2.h)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="implement_dynamic"></a>  IMPLEMENT_DYNAMIC

Generuje kod C++ niezbędnych do dynamiczny `CObject`-pochodne klasy przy użyciu dostępu w czasie wykonywania do nazwy klasy i pozycji w hierarchii.

```
IMPLEMENT_DYNAMIC(class_name, base_class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Rzeczywista nazwa klasy.

*base_class_name*<br/>
Nazwa klasy bazowej.

### <a name="remarks"></a>Uwagi

Użyj IMPLEMENT_DYNAMIC — makro w .cpp module, a następnie połącz wynikowy kod obiektu tylko raz.

Aby uzyskać więcej informacji, zobacz [tematy klasa CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCObjectSample#2](../../mfc/codesnippet/cpp/run-time-object-model-services_3.h)]

[!code-cpp[NVC_MFCCObjectSample#3](../../mfc/codesnippet/cpp/run-time-object-model-services_4.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="implement_dyncreate"></a>  IMPLEMENT_DYNCREATE

Włącza obiektów `CObject`-pochodne klasy można tworzyć dynamicznie przy uruchomieniu czasu, gdy jest używane z DECLARE_DYNCREATE — makro.

```
IMPLEMENT_DYNCREATE(class_name, base_class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Rzeczywista nazwa klasy.

*base_class_name*<br/>
Rzeczywista nazwa klasy bazowej.

### <a name="remarks"></a>Uwagi

Środowisko wykorzystuje tę możliwość do tworzenia nowych obiektów dynamicznie, na przykład, gdy obiekt zostanie odczytanych z dysku podczas serializacji. Dodaj IMPLEMENT_DYNCREATE — makro w pliku implementacji klasy. Aby uzyskać więcej informacji, zobacz [tematy klasa CObject](../../mfc/using-cobject.md).

Jeśli używasz DECLARE_DYNCREATE i IMPLEMENT_DYNCREATE makra, następnie można użyć makra RUNTIME_CLASS i `CObject::IsKindOf` funkcja elementu członkowskiego, aby określić klasę obiektów w czasie wykonywania.

Jeśli DECLARE_DYNCREATE jest uwzględniona w deklaracji klasy, IMPLEMENT_DYNCREATE muszą być zawarte w implementacji klasy.

Należy pamiętać, że ta definicja makra spowoduje wywołanie domyślnego konstruktora dla klasy. Jeśli Konstruktor nietrywialnymi jawnie jest zaimplementowany przez klasę, musi również jawnie implementuje ona również konstruktora domyślnego. Konstruktor domyślny, mogą być dodawane do klasy **prywatnej** lub **chronione** sekcji elementu członkowskiego, aby uniemożliwić wywoływana z poza Implementacja klasy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCObjectSample#22](../../mfc/codesnippet/cpp/run-time-object-model-services_5.h)]

[!code-cpp[NVC_MFCCObjectSample#23](../../mfc/codesnippet/cpp/run-time-object-model-services_6.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="implement_olecreate_flags"></a>  IMPLEMENT_OLECREATE_FLAGS

Albo to makro lub [IMPLEMENT_OLECREATE](#implement_olecreate) musi znajdować się w pliku implementacji dla każdej klasy, która używa DECLARE_OLECREATE.

### <a name="syntax"></a>Składnia

```
IMPLEMENT_OLECREATE_FLAGS( class_name, external_name, nFlags,
    l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Rzeczywista nazwa klasy.

*external_name*<br/>
Nazwa obiektu widoczne dla innych aplikacji (ujęty w znaki cudzysłowu).

*nFlags*<br/>
Zawiera co najmniej jeden z następujących flag:

   - `afxRegInsertable` Zapewnia kontrolę pojawią się w oknie dialogowym Wstaw obiekt dla obiektów OLE.
   - `afxRegApartmentThreading` Ustawia model wątkowości w rejestrze, aby ThreadingModel = typu Apartment.
   - `afxRegFreeThreading` Ustawia model wątkowości w rejestrze, aby ThreadingModel = bezpłatna.

         You can combine the two flags `afxRegApartmentThreading` and `afxRegFreeThreading` to set ThreadingModel=Both. See [InprocServer32](/windows/desktop/com/inprocserver32) in the Windows SDK for more information on threading model registration.

*l*, *w1*, *w2*, *b1*, *b2*, *b3*, *b4* , *b5*, *b6*, *b7*, *b8* składniki CLSID tej klasy.

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Jeśli używasz IMPLEMENT_OLECREATE_FLAGS, można określić jakiego modelu wątków, które obsługuje Twój obiekt, za pomocą *nFlags* parametru. Do obsługi tylko treading pojedynczego modelu, należy użyć makro IMPLEMENT_OLECREATE.

Zewnętrzna nazwa jest identyfikator widoczne dla innych aplikacji. Aplikacje klienckie korzystają zewnętrzną nazwę do obiektu tej klasy należy poprosić serwera automatyzacji.

Identyfikator klasy OLE jest unikatowym identyfikatorem 128-bitowego dla obiektu. Składa się z jednego **długie**, dwa **WORD**s i osiem **BAJTÓW**s, reprezentowane przez *l*, *w1*, *w2*, i *b1* za pośrednictwem *b8* w opisie składni. Kreatorzy Kreatora aplikacji, a kod tworzy unikatowych identyfikatorów klas OLE zgodnie z potrzebami.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

## <a name="implementolectltype"></a>IMPLEMENT_OLECTLTYPE

Implementuje `GetUserTypeNameID` i `GetMiscStatus` funkcji składowych klasy kontrolki.

### <a name="syntax"></a>Składnia

```
DECLARE_OLECTLTYPE( class_name, idsUserTypeName, dwOleMisc )
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Nazwa klasy kontrolki.

*idsUserTypeName*<br/>
Identyfikator zasobu ciągu zawierającego nazwę zewnętrznego kontrolki.

*dwOleMisc*<br/>
Wyliczenie zawierający jedną lub więcej flag. Aby uzyskać więcej informacji na temat tego wyliczenia, zobacz [OLEMISC](/windows/desktop/api/oleidl/ne-oleidl-tagolemisc) w zestawie Windows SDK.

### <a name="remarks"></a>Uwagi

Oprócz IMPLEMENT_OLECTLTYPE należy dodać DECLARE_OLECTLTYPE — makro do sterowania deklaracją klasy.

`GetUserTypeNameID` Funkcja elementu członkowskiego zwraca ciąg zasobu, który identyfikuje klasy kontrolki. `GetMiscStatus` Zwraca bitów OLEMISC kontrolki. To wyliczenie określa zbiór ustawień opisujących różne właściwości kontrolki. Aby uzyskać pełny opis ustawienia OLEMISC zobacz [OLEMISC](/windows/desktop/api/oleidl/ne-oleidl-tagolemisc) w zestawie Windows SDK.

> [!NOTE]
>  Ustawieniami domyślnymi używanymi przez ActiveX ControlWizard są następujące: OLEMISC_ACTIVATEWHENVISIBLE OLEMISC_SETCLIENTSITEFIRST, OLEMISC_INSIDEOUT, OLEMISC_CANTLINKINSIDE i OLEMISC_RECOMPOSEONRESIZE.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxctl.h

##  <a name="implement_serial"></a>  IMPLEMENT_SERIAL

Generuje kod C++ niezbędnych do dynamiczny `CObject`-pochodne klasy przy użyciu dostępu w czasie wykonywania do nazwy klasy i pozycji w hierarchii.

```
IMPLEMENT_SERIAL(class_name, base_class_name, wSchema)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Rzeczywista nazwa klasy.

*base_class_name*<br/>
Nazwa klasy bazowej.

*wSchema*<br/>
UINT "numer wersji" będzie zapisywana w warstwie archiwum, aby umożliwić programowi deserializacji do identyfikowania i obsługi danych utworzonych przez program we wcześniejszej wersji. Liczba schematu klasy nie może być -1.

### <a name="remarks"></a>Uwagi

W .cpp module; użyć IMPLEMENT_SERIAL — makro następnie połącz wynikowy kod obiektu tylko raz.

Aby wyeksportować automatycznie, można użyć makra AFX_API `CArchive` operator wyodrębniania dla klas, które używają DECLARE_SERIAL i IMPLEMENT_SERIAL makr. Dopasowywanie deklaracji klasy (znajdujący się w pliku .h) z następującym kodem:

[!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]

Aby uzyskać więcej informacji, zobacz [tematy klasa CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCObjectSample#24](../../mfc/codesnippet/cpp/run-time-object-model-services_7.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="runtime_class"></a>  RUNTIME_CLASS

Pobiera w strukturze klas środowiska wykonawczego od nazwy klasy języka C++.

```
RUNTIME_CLASS(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Rzeczywista nazwa klasy (nie ujęta w znaki cudzysłowu).

### <a name="remarks"></a>Uwagi

RUNTIME_CLASS zwraca wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) struktury z klasą określoną przez *class_name*. Tylko `CObject`-klasy pochodne zadeklarowane za pomocą DECLARE_DYNAMIC, DECLARE_DYNCREATE lub DECLARE_SERIAL zwróci wskaźniki do `CRuntimeClass` struktury.

Aby uzyskać więcej informacji, zobacz [tematy klasa CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCObjectSample#25](../../mfc/codesnippet/cpp/run-time-object-model-services_8.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

##  <a name="declare_olecreate"></a>  DECLARE_OLECREATE

Włącza obiektów `CCmdTarget`-pochodne klasy, które ma zostać utworzony za pomocą automatyzacji OLE.

```
DECLARE_OLECREATE(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Rzeczywista nazwa klasy.

### <a name="remarks"></a>Uwagi

To makro umożliwia innych aplikacji z obsługą OLE do tworzenia obiektów tego typu.

Dodaj DECLARE_OLECREATE — makro w module .h klasy, a następnie dołącz ten moduł we wszystkich modułach .cpp, którzy potrzebują dostępu do obiektów tej klasy.

Jeśli DECLARE_OLECREATE jest uwzględniona w deklaracji klasy, makro IMPLEMENT_OLECREATE muszą być zawarte w implementacji klasy. Za pomocą DECLARE_OLECREATE deklaracji klasy, należy również użyć DECLARE_DYNCREATE lub DECLARE_SERIAL.

### <a name="requirements"></a>Wymagania

**Nagłówek**: afxdisp.h

##  <a name="implement_olecreate"></a>  IMPLEMENT_OLECREATE

Albo to makro lub [IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags) musi znajdować się w pliku implementacji dla każdej klasy, która używa `DECLARE_OLECREATE`.

```
IMPLEMENT_OLECREATE(class_name, external_name, l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Rzeczywista nazwa klasy.

*external_name*<br/>
Nazwa obiektu widoczne dla innych aplikacji (ujęty w znaki cudzysłowu).

*l*, *w1*, *w2*, *b1*, *b2*, *b3*, *b4* , *b5*, *b6*, *b7*, *b8* składniki CLSID tej klasy.

### <a name="remarks"></a>Uwagi

> [!NOTE]
>  Jeśli używasz IMPLEMENT_OLECREATE, domyślnie obsługuje się tylko pojedynczego modelu wątkowości. Jeśli używasz IMPLEMENT_OLECREATE_FLAGS, można określić jakiego modelu wątków, które obsługuje Twój obiekt, za pomocą *nFlags* parametru.

Zewnętrzna nazwa jest identyfikator widoczne dla innych aplikacji. Aplikacje klienckie korzystają zewnętrzną nazwę do obiektu tej klasy należy poprosić serwera automatyzacji.

Identyfikator klasy OLE jest unikatowym identyfikatorem 128-bitowego dla obiektu. Składa się z jednego **długie**, dwa **WORD**s i osiem **BAJTÓW**s, reprezentowane przez *l*, *w1*, *w2*, i *b1* za pośrednictwem *b8* w opisie składni. Kreatorzy Kreatora aplikacji, a kod tworzy unikatowych identyfikatorów klas OLE zgodnie z potrzebami.

### <a name="requirements"></a>Wymagania

**Nagłówek**: afxdisp.h

## <a name="see-also"></a>Zobacz także

[Makra i funkcje globalne](mfc-macros-and-globals.md)<br/>
[Izolacja biblioteki formantów wspólnych MFC](../isolation-of-the-mfc-common-controls-library.md)<br/>
[Identyfikator CLSID klucza](/windows/desktop/com/clsid-key-hklm)
