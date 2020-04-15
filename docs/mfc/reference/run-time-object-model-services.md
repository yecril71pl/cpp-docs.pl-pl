---
title: Usługi modelu obiektów czasu wykonywania
ms.date: 03/27/2019
helpviewer_keywords:
- run-time object model services macros
ms.assetid: 4a3e79df-2ee3-43a4-8193-20298828de85
ms.openlocfilehash: f1cefdad368ebcd006dcb4ecf653247147f36d03
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372942"
---
# <a name="run-time-object-model-services"></a>Usługi modelu obiektów czasu wykonywania

Klasy [CObject](../../mfc/reference/cobject-class.md) i [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) hermetyzują kilka usług obiektów, w tym dostęp do informacji o klasie w czasie wykonywania, serializację i tworzenie obiektów dynamicznych. Wszystkie klasy pochodzące z `CObject` dziedziczą tę funkcję.

Dostęp do informacji o klasie w czasie wykonywania umożliwia określenie informacji o klasie obiektu w czasie wykonywania. Możliwość określenia klasy obiektu w czasie wykonywania jest przydatna, gdy potrzebne jest dodatkowe sprawdzanie typu argumentów funkcji i gdy należy napisać kod specjalnego przeznaczenia na podstawie klasy obiektu. Informacje o klasie w czasie wykonywania nie jest obsługiwany bezpośrednio przez język C++.

Serializacja to proces zapisywania lub odczytywania zawartości obiektu do lub z pliku. Serializacji można używać do przechowywania zawartości obiektu, nawet po zakończeniu aplikacji. Obiekt można następnie odczytać z pliku po ponownym uruchomieniu aplikacji. Takie obiekty danych są uważane za "trwałe".

Tworzenie obiektu dynamicznego umożliwia utworzenie obiektu określonej klasy w czasie wykonywania. Na przykład obiekty dokumentu, widoku i ramki muszą obsługiwać tworzenie dynamiczne, ponieważ struktura musi je dynamicznie tworzyć.

W poniższej tabeli wymieniono makra MFC, które obsługują informacje o klasie w czasie wykonywania, serializacji i tworzenia dynamicznego.

Aby uzyskać więcej informacji na temat tych usług obiektów w czasie wykonywania i serializacji, zobacz artykuł [CObject Klasa: Uzyskiwanie dostępu do informacji o klasie w czasie wykonywania](../../mfc/accessing-run-time-class-information.md).

### <a name="run-time-object-model-services-macros"></a>Makra usług modelu obiektów w czasie wykonywania

|||
|-|-|
|[DECLARE_DYNAMIC](#declare_dynamic)|Umożliwia dostęp do informacji o klasie w czasie wykonywania (musi być używany w deklaracji klasy).|
|[Declare_dyncreate](#declare_dyncreate)|Umożliwia dynamiczne tworzenie i dostęp do informacji o klasie w czasie wykonywania (musi być używany w deklaracji klasy).|
|[Declare_serial](#declare_serial)|Włącza serializacji i dostępu do informacji o klasie w czasie wykonywania (musi być używany w deklaracji klasy).|
|[Implement_dynamic](#implement_dynamic)|Umożliwia dostęp do informacji o klasie w czasie wykonywania (musi być używany w implementacji klasy).|
|[Implement_dyncreate](#implement_dyncreate)|Umożliwia dynamiczne tworzenie i dostęp do informacji w czasie wykonywania (musi być używany w implementacji klasy).|
|[Implement_serial](#implement_serial)|Umożliwia serializację i dostęp do informacji o klasie w czasie wykonywania (musi być używany w implementacji klasy).|
|[RUNTIME_CLASS](#runtime_class)|Zwraca `CRuntimeClass` strukturę, która odpowiada nazwanej klasie.|

Ole często wymaga dynamicznego tworzenia obiektów w czasie wykonywania. Na przykład aplikacja serwera OLE musi być w stanie dynamicznie tworzyć elementy OLE w odpowiedzi na żądanie od klienta. Podobnie serwer automatyzacji musi być w stanie tworzyć elementy w odpowiedzi na żądania od klientów automatyzacji.

Biblioteka klas Programu Microsoft Foundation zawiera dwa makra specyficzne dla ole.

### <a name="dynamic-creation-of-ole-objects"></a>Dynamiczne tworzenie obiektów OLE

|||
|-|-|
|[AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)|Określa, czy biblioteka common controls implementuje określony interfejs API.|
|[AFX_COMCTL32_IF_EXISTS2](#afx_comctl32_if_exists2)|Określa, czy biblioteka common controls implementuje określony interfejs API.|
|[DECLARE_OLECREATE](#declare_olecreate)|Umożliwia tworzenie obiektów za pomocą automatyzacji OLE.|
|[DECLARE_OLECTLTYPE](#declare_olectltype)|Deklaruje `GetUserTypeNameID` i `GetMiscStatus` funkcje członkowskie klasy kontroli.|
|[DECLARE_PROPPAGEIDS](#declare_proppageids)|Deklaruje, że formant OLE zawiera listę stron właściwości, aby wyświetlić jego właściwości.|
|[IMPLEMENT_OLECREATE](#implement_olecreate)|Umożliwia tworzenie obiektów przez system OLE.|
|[IMPLEMENT_OLECTLTYPE](#implement_olectltype)|Implementuje `GetUserTypeNameID` funkcje i `GetMiscStatus` członków klasy kontroli.|
|[IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags)|To makro lub [IMPLEMENT_OLECREATE](#implement_olecreate) muszą być wyświetlane w pliku implementacji `DECLARE_OLECREATE`dla każdej klasy, która używa . |

## <a name="afx_comctl32_if_exists"></a><a name="afx_comctl32_if_exists"></a>AFX_COMCTL32_IF_EXISTS

Określa, czy biblioteka common controls implementuje określony interfejs API.

### <a name="syntax"></a>Składnia

```
AFX_COMCTL32_IF_EXISTS(  proc );
```

### <a name="parameters"></a>Parametry

*Proc*<br/>
Wskaźnik do ciągu zakończonego z wartością null zawierającego nazwę funkcji lub określa wartość porządkową funkcji. Jeśli ten parametr jest wartością porządkową, musi być w słowie niskiego rzędu; słowo wysokiego rzędu musi wynosić zero. Ten parametr musi być w Unicode.

### <a name="remarks"></a>Uwagi

Użyj tego makra, aby określić, czy biblioteka Wspólnych formanty jest funkcją określoną przez *proc* (zamiast wywoływania [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress).

### <a name="requirements"></a>Wymagania

afxcomctl32.h, afxcomctl32.inl

## <a name="afx_comctl32_if_exists2"></a><a name="afx_comctl32_if_exists2"></a>AFX_COMCTL32_IF_EXISTS2

Określa, czy biblioteka Common Controls implementuje określony interfejs API (jest to wersja [unicode AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)).

### <a name="syntax"></a>Składnia

```
AFX_COMCTL32_IF_EXISTS2( proc );
```

### <a name="parameters"></a>Parametry

*Proc*<br/>
Wskaźnik do ciągu zakończonego z wartością null zawierającego nazwę funkcji lub określa wartość porządkową funkcji. Jeśli ten parametr jest wartością porządkową, musi być w słowie niskiego rzędu; słowo wysokiego rzędu musi wynosić zero. Ten parametr musi być w Unicode.

### <a name="remarks"></a>Uwagi

Użyj tego makra, aby określić, czy biblioteka Wspólnych formanty jest funkcją określoną przez *proc* (zamiast wywoływania [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress). To makro jest wersją unicode AFX_COMCTL32_IF_EXISTS.

### <a name="requirements"></a>Wymagania

afxcomctl32.h, afxcomctl32.inl

## <a name="declare_dynamic"></a><a name="declare_dynamic"></a>DECLARE_DYNAMIC

Dodaje możliwość dostępu do informacji w czasie wykonywania o klasie obiektu `CObject`podczas wyprowadzania klasy z programu .

```
DECLARE_DYNAMIC(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Rzeczywista nazwa klasy.

### <a name="remarks"></a>Uwagi

Dodaj makro DECLARE_DYNAMIC do modułu nagłówka (.h) dla klasy, a następnie uwzględnij ten moduł we wszystkich modułach .cpp, które potrzebują dostępu do obiektów tej klasy.

Jeśli DECLARE_ makra DYNAMIC i IMPLEMENT_DYNAMIC w sposób opisany, można użyć makra RUNTIME_CLASS i `CObject::IsKindOf` funkcji do określenia klasy obiektów w czasie wykonywania.

Jeśli DECLARE_DYNAMIC jest uwzględniony w deklaracji klasy, IMPLEMENT_DYNAMIC musi być uwzględniony w implementacji klasy.

Aby uzyskać więcej informacji na temat makra DECLARE_DYNAMIC, zobacz [Tematy zajęć CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Przykład

Zobacz przykład [IMPLEMENT_DYNAMIC](#implement_dynamic).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="declare_dyncreate"></a><a name="declare_dyncreate"></a>Declare_dyncreate

Umożliwia dynamiczne tworzenie obiektów klas `CObject`pochodnych w czasie wykonywania.

```
DECLARE_DYNCREATE(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Rzeczywista nazwa klasy.

### <a name="remarks"></a>Uwagi

Struktura używa tej możliwości do dynamicznego tworzenia nowych obiektów. Na przykład nowy widok utworzony po otwarciu nowego dokumentu. Klasy dokumentu, widoku i ramki powinny obsługiwać dynamiczne tworzenie, ponieważ struktura musi je dynamicznie tworzyć.

Dodaj makro DECLARE_DYNCREATE w module .h dla klasy, a następnie dołącz ten moduł do wszystkich modułów .cpp, które potrzebują dostępu do obiektów tej klasy.

Jeśli DECLARE_DYNCREATE jest uwzględniony w deklaracji klasy, IMPLEMENT_DYNCREATE musi być uwzględniony w implementacji klasy.

Aby uzyskać więcej informacji na temat makra DECLARE_DYNCREATE, zobacz [Tematy zajęć CObject](../../mfc/using-cobject.md).

> [!NOTE]
> Makro DECLARE_DYNCREATE zawiera wszystkie funkcje DECLARE_DYNAMIC.

### <a name="example"></a>Przykład

Zobacz przykład [IMPLEMENT_DYNCREATE](#implement_dyncreate).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="declare_olectltype"></a><a name="declare_olectltype"></a>DECLARE_OLECTLTYPE

Deklaruje `GetUserTypeNameID` i `GetMiscStatus` funkcje członkowskie klasy kontroli.

### <a name="syntax"></a>Składnia

```
DECLARE_OLECTLTYPE( class_name )
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Nazwa klasy formantu.

### <a name="remarks"></a>Uwagi

`GetUserTypeNameID`i `GetMiscStatus` są czystymi funkcjami wirtualnymi, zadeklarowane w `COleControl`. Ponieważ te funkcje są czysto wirtualne, muszą zostać zastąpione w klasie kontroli. Oprócz DECLARE_OLECTLTYPE należy dodać makro IMPLEMENT_OLECTLTYPE do deklaracji klasy kontrolnej.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxctl.h

## <a name="declare_proppageids"></a><a name="declare_proppageids"></a>DECLARE_PROPPAGEIDS

Deklaruje, że formant OLE zawiera listę stron właściwości, aby wyświetlić jego właściwości.

### <a name="syntax"></a>Składnia

```
DECLARE_PROPPAGEIDS( class_name )
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Nazwa klasy formantu, która jest właścicielem stron właściwości.

### <a name="remarks"></a>Uwagi

Użyj `DECLARE_PROPPAGEIDS` makra na końcu deklaracji klasy. Następnie w pliku .cpp, który definiuje funkcje członkowskie `BEGIN_PROPPAGEIDS` dla klasy, użyj makra, wpisów makr `END_PROPPAGEIDS` dla każdej ze stron właściwości formantu i makra, aby zadeklarować koniec listy stron właściwości.

Aby uzyskać więcej informacji na temat stron właściwości, zobacz artykuł [ActiveX Controls: Property Pages](../mfc-activex-controls-property-pages.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxctl.h

## <a name="declare_serial"></a><a name="declare_serial"></a>Declare_serial

Generuje kod nagłówka C++ `CObject`niezbędne dla klasy pochodnej, które mogą być serializowane.

```
DECLARE_SERIAL(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Rzeczywista nazwa klasy.

### <a name="remarks"></a>Uwagi

Serializacja to proces pisania lub odczytywania zawartości obiektu do i z pliku.

Użyj makra DECLARE_SERIAL w module .h, a następnie dołącz ten moduł do wszystkich modułów .cpp, które potrzebują dostępu do obiektów tej klasy.

Jeśli DECLARE_SERIAL jest uwzględniony w deklaracji klasy, IMPLEMENT_SERIAL musi być uwzględniony w implementacji klasy.

Makro DECLARE_SERIAL zawiera wszystkie funkcje DECLARE_DYNAMIC i DECLARE_DYNCREATE.

Za pomocą makra AFX_API można automatycznie wyeksportować operatora `CArchive` wyodrębniania dla klas korzystających z makr DECLARE_SERIAL i IMPLEMENT_SERIAL. Wspornik deklaracji klas (znajdujących się w pliku .h) z następującym kodem:

[!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]

Aby uzyskać więcej informacji na temat makra DECLARE_SERIAL, zobacz [Tematy zajęć CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCObjectSample#21](../../mfc/codesnippet/cpp/run-time-object-model-services_2.h)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="implement_dynamic"></a><a name="implement_dynamic"></a>Implement_dynamic

Generuje kod C++ niezbędny `CObject`dla klasy dynamicznej pochodnej z dostępem w czasie wykonywania do nazwy i pozycji klasy w hierarchii.

```
IMPLEMENT_DYNAMIC(class_name, base_class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Rzeczywista nazwa klasy.

*base_class_name*<br/>
Nazwa klasy podstawowej.

### <a name="remarks"></a>Uwagi

Użyj makra IMPLEMENT_DYNAMIC w module .cpp, a następnie połącz wynikowy kod obiektu tylko raz.

Aby uzyskać więcej informacji, zobacz [Tematy zajęć CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCObjectSample#2](../../mfc/codesnippet/cpp/run-time-object-model-services_3.h)]

[!code-cpp[NVC_MFCCObjectSample#3](../../mfc/codesnippet/cpp/run-time-object-model-services_4.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="implement_dyncreate"></a><a name="implement_dyncreate"></a>Implement_dyncreate

Umożliwia dynamiczne tworzenie obiektów klas pochodnych `CObject`w czasie wykonywania, gdy są używane z makrą DECLARE_DYNCREATE.

```
IMPLEMENT_DYNCREATE(class_name, base_class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Rzeczywista nazwa klasy.

*base_class_name*<br/>
Rzeczywista nazwa klasy podstawowej.

### <a name="remarks"></a>Uwagi

Struktura używa tej możliwości do tworzenia nowych obiektów dynamicznie, na przykład, gdy odczytuje obiekt z dysku podczas serializacji. Dodaj makro IMPLEMENT_DYNCREATE w pliku implementacji klasy. Aby uzyskać więcej informacji, zobacz [Tematy zajęć CObject](../../mfc/using-cobject.md).

Jeśli używasz makr DECLARE_DYNCREATE i IMPLEMENT_DYNCREATE, możesz użyć makra RUNTIME_CLASS i funkcji `CObject::IsKindOf` elementu członkowskiego, aby określić klasę obiektów w czasie wykonywania.

Jeśli DECLARE_DYNCREATE jest uwzględniony w deklaracji klasy, IMPLEMENT_DYNCREATE musi być uwzględniony w implementacji klasy.

Należy zauważyć, że ta definicja makra wywoła domyślny konstruktor dla klasy. Jeśli konstruktor nietrywialny jest jawnie implementowane przez klasę, musi również jawnie implementować domyślny konstruktora, jak również. Konstruktora domyślnego można dodać do klasy **sekcji prywatnych** lub **chronionych** elementów członkowskich, aby zapobiec jego wywoływaniu spoza implementacji klasy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCObjectSample#22](../../mfc/codesnippet/cpp/run-time-object-model-services_5.h)]

[!code-cpp[NVC_MFCCObjectSample#23](../../mfc/codesnippet/cpp/run-time-object-model-services_6.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="implement_olecreate_flags"></a><a name="implement_olecreate_flags"></a>IMPLEMENT_OLECREATE_FLAGS

To makro lub [IMPLEMENT_OLECREATE](#implement_olecreate) muszą być wyświetlane w pliku implementacji dla każdej klasy, która używa DECLARE_OLECREATE.

### <a name="syntax"></a>Składnia

```
IMPLEMENT_OLECREATE_FLAGS( class_name, external_name, nFlags,
    l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Rzeczywista nazwa klasy.

*external_name*<br/>
Nazwa obiektu jest widoczna dla innych aplikacji (ujęta w cudzysłów).

*nPłgi*<br/>
Zawiera co najmniej jedną z następujących flag:

- `afxRegInsertable`Umożliwia wyświetlenie formantu w oknie dialogowym Wstawianie obiektu dla obiektów OLE.
- `afxRegApartmentThreading`Ustawia model wątków w rejestrze na ThreadingModel=Apartment.
- `afxRegFreeThreading`Ustawia model wątków w rejestrze na ThreadingModel=Free.

Można połączyć dwie `afxRegApartmentThreading` `afxRegFreeThreading` flagi i ustawić ThreadingModel=Both. Zobacz [InprocServer32](/windows/win32/com/inprocserver32) w windows SDK, aby uzyskać więcej informacji na temat rejestracji modelu wątkowości.

*l*, *w1*, *w2*, *b1*, *b2*, *b3*, *b4*, *b5*, *b6*, *b7*, *b8* Składniki clsid klasy.

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Jeśli używasz IMPLEMENT_OLECREATE_FLAGS, można określić, który model wątków obsługuje obiekt przy użyciu *nFlags* parametru. Jeśli chcesz obsługiwać tylko model jednośmikła, użyj IMPLEMENT_OLECREATE.

Nazwa zewnętrzna jest identyfikatorem narażonym na inne aplikacje. Aplikacje klienckie używają nazwy zewnętrznej do żądania obiektu tej klasy z serwera automatyzacji.

Identyfikator klasy OLE jest unikatowym identyfikatorem 128-bitowym dla obiektu. Składa się z jednego **długiego**, dwa **WORD**s i osiem **BYTE**s, reprezentowane przez *l*, *w1*, *w2*i *b1* do *b8* w opisie składni. Kreator aplikacji i kreatorzy kodu tworzą unikatowe identyfikatory klas OLE zgodnie z wymaganiami.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

## <a name="implement_olectltype"></a><a name="implement_olectltype"></a>IMPLEMENT_OLECTLTYPE

Implementuje `GetUserTypeNameID` funkcje i `GetMiscStatus` członków klasy kontroli.

### <a name="syntax"></a>Składnia

```
DECLARE_OLECTLTYPE( class_name, idsUserTypeName, dwOleMisc )
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Nazwa klasy formantu.

*nazwa idsUserTypeName*<br/>
Identyfikator zasobu ciągu zawierającego nazwę zewnętrzną formantu.

*dwOleMisc (DwoleMisc)*<br/>
Wyliczenie zawierające co najmniej jedną flagę. Aby uzyskać więcej informacji na temat tego wyliczenia, zobacz [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) w windows SDK.

### <a name="remarks"></a>Uwagi

Oprócz IMPLEMENT_OLECTLTYPE należy dodać makro DECLARE_OLECTLTYPE do deklaracji klasy kontrolnej.

Funkcja `GetUserTypeNameID` elementu członkowskiego zwraca ciąg zasobu, który identyfikuje klasę kontrolną. `GetMiscStatus`zwraca bity OLEMISC dla formantu. To wyliczenie określa zbiór ustawień opisujących różne cechy formantu. Aby uzyskać pełny opis ustawień OLEMISC, zobacz [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) w panelu Windows SDK.

> [!NOTE]
> Domyślne ustawienia używane przez ActiveX ControlWizard to: OLEMISC_ACTIVATEWHENVISIBLE, OLEMISC_SETCLIENTSITEFIRST, OLEMISC_INSIDEOUT, OLEMISC_CANTLINKINSIDE i OLEMISC_RECOMPOSEONRESIZE.

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxctl.h

## <a name="implement_serial"></a><a name="implement_serial"></a>Implement_serial

Generuje kod C++ niezbędny `CObject`dla klasy dynamicznej pochodnej z dostępem w czasie wykonywania do nazwy i pozycji klasy w hierarchii.

```
IMPLEMENT_SERIAL(class_name, base_class_name, wSchema)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Rzeczywista nazwa klasy.

*base_class_name*<br/>
Nazwa klasy podstawowej.

*wSchema*<br/>
UINT "numer wersji", który zostanie zakodowany w archiwum, aby umożliwić deserializacji programu do identyfikowania i obsługi danych utworzonych przez wcześniejsze wersje programu. Numer schematu klasy nie może być -1.

### <a name="remarks"></a>Uwagi

Użyj makra IMPLEMENT_SERIAL w module .cpp; następnie połącz wynikowy kod obiektu tylko raz.

Za pomocą makra AFX_API można automatycznie wyeksportować operatora `CArchive` wyodrębniania dla klas korzystających z makr DECLARE_SERIAL i IMPLEMENT_SERIAL. Wspornik deklaracji klas (znajdujących się w pliku .h) z następującym kodem:

[!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]

Aby uzyskać więcej informacji, zobacz [tematy zajęć CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCObjectSample#24](../../mfc/codesnippet/cpp/run-time-object-model-services_7.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="runtime_class"></a><a name="runtime_class"></a>RUNTIME_CLASS

Pobiera strukturę klasy w czasie wykonywania od nazwy klasy C++.

```
RUNTIME_CLASS(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Rzeczywista nazwa klasy (nie ujęta w cudzysłów).

### <a name="remarks"></a>Uwagi

RUNTIME_CLASS zwraca wskaźnik do [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) struktury dla klasy określonej przez *class_name*. Tylko `CObject`klasy pochodne zadeklarowane za pomocą DECLARE_DYNAMIC, DECLARE_DYNCREATE lub DECLARE_SERIAL zwróci wskaźniki do `CRuntimeClass` struktury.

Aby uzyskać więcej informacji, zobacz [Tematy zajęć CObject](../../mfc/using-cobject.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_MFCCObjectSample#25](../../mfc/codesnippet/cpp/run-time-object-model-services_8.cpp)]

### <a name="requirements"></a>Wymagania

**Nagłówek:** afx.h

## <a name="declare_olecreate"></a><a name="declare_olecreate"></a>DECLARE_OLECREATE

Umożliwia tworzenie `CCmdTarget`obiektów klas pochodnych za pomocą automatyzacji OLE.

```
DECLARE_OLECREATE(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Rzeczywista nazwa klasy.

### <a name="remarks"></a>Uwagi

To makro umożliwia innym aplikacjom obsługującym ole tworzenie obiektów tego typu.

Dodaj makro DECLARE_OLECREATE w module .h dla klasy, a następnie dołącz ten moduł do wszystkich modułów .cpp, które potrzebują dostępu do obiektów tej klasy.

Jeśli DECLARE_OLECREATE jest uwzględniony w deklaracji klasy, IMPLEMENT_OLECREATE musi być uwzględniony w implementacji klasy. Deklaracja klasy przy użyciu DECLARE_OLECREATE musi również używać DECLARE_DYNCREATE lub DECLARE_SERIAL.

### <a name="requirements"></a>Wymagania

**Nagłówek**: afxdisp.h

## <a name="implement_olecreate"></a><a name="implement_olecreate"></a>IMPLEMENT_OLECREATE

To makro lub [IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags) muszą pojawić się w pliku implementacji `DECLARE_OLECREATE`dla każdej klasy, która używa .

```
IMPLEMENT_OLECREATE(class_name, external_name, l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Rzeczywista nazwa klasy.

*external_name*<br/>
Nazwa obiektu jest widoczna dla innych aplikacji (ujęta w cudzysłów).

*l*, *w1*, *w2*, *b1*, *b2*, *b3*, *b4*, *b5*, *b6*, *b7*, *b8* Składniki clsid klasy.

### <a name="remarks"></a>Uwagi

> [!NOTE]
> Jeśli używasz IMPLEMENT_OLECREATE, domyślnie obsługuje tylko modelu jednowątkowego wątku. Jeśli używasz IMPLEMENT_OLECREATE_FLAGS, można określić, który model wątków obsługuje obiekt przy użyciu *nFlags* parametru.

Nazwa zewnętrzna jest identyfikatorem narażonym na inne aplikacje. Aplikacje klienckie używają nazwy zewnętrznej do żądania obiektu tej klasy z serwera automatyzacji.

Identyfikator klasy OLE jest unikatowym identyfikatorem 128-bitowym dla obiektu. Składa się z jednego **długiego**, dwa **WORD**s i osiem **BYTE**s, reprezentowane przez *l*, *w1*, *w2*i *b1* do *b8* w opisie składni. Kreator aplikacji i kreatorzy kodu tworzą unikatowe identyfikatory klas OLE zgodnie z wymaganiami.

### <a name="requirements"></a>Wymagania

**Nagłówek**: afxdisp.h

## <a name="see-also"></a>Zobacz też

[Makra i globals](mfc-macros-and-globals.md)<br/>
[Izolacja biblioteki formantów wspólnych MFC](../isolation-of-the-mfc-common-controls-library.md)<br/>
[Klucz CLSID](/windows/win32/com/clsid-key-hklm)
