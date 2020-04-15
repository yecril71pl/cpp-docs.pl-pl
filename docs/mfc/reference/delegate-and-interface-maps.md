---
title: Delegowanie i mapowanie interfejsu (MFC)
ms.date: 03/30/2017
helpviewer_keywords:
- delegate map macros [MFC]
- event map macros [MFC]
- interface map macros [MFC]
ms.assetid: 3840e642-ff7d-4bdc-998b-c7d8fc50890e
ms.openlocfilehash: e08597d024f5e3a74dcf47363ad3de0aa60cf6c0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365836"
---
# <a name="delegate-and-interface-map-macros"></a>Makra delegata i mapy interfejsu

MFC obsługuje te makra dla map delegata i interfejsu:

|||
|-|-|
|[BEGIN_DELEGATE_MAP](#begin_delegate_map)|Rozpoczyna mapę delegata.|
|[BEGIN_INTERFACE_MAP](#begin_interface_map)|Rozpoczyna definicję mapy interfejsu.|
|[Delegat CommandHandler](#commandhandler)|Rejestruje metody wywołania zwrotnego ze źródłem polecenia.  |
|[END_DELEGATE_MAP](#end_delegate_map)|Kończy mapę delegata.|
|[END_INTERFACE_MAP](#end_interface_map)|Kończy mapę interfejsu w pliku implementacji. |
|[EVENT_DELEGATE_ENTRY](#event_delegate_entry)|Tworzy wpis na mapie pełnomocnika.|
|[Interface_part](#interface_part)|Używane między makro BEGIN_INTERFACE_MAP a makro END_INTERFACE_MAP dla każdego interfejsu, który będzie obsługiwał obiekt.|
|[MAKE_DELEGATE](#make_delegate)|Dołącza program obsługi zdarzeń do formantu zarządzanego.|

## <a name="begin_delegate_map"></a><a name="begin_delegate_map"></a>BEGIN_DELEGATE_MAP

Rozpoczyna mapę delegata.

### <a name="syntax"></a>Składnia

```
BEGIN_DELEGATE_MAP(  CLASS );
```

### <a name="parameters"></a>Parametry

*Klasa*<br/>
Klasa, w której hostowany jest formant zarządzany.

### <a name="remarks"></a>Uwagi

To makro oznacza początek listy wpisów delegata, które tworzą mapę pełnomocnika. Na przykład, jak to makro jest używane, zobacz [EVENT_DELEGATE_ENTRY](#event_delegate_entry).

### <a name="requirements"></a>Wymagania

**Nagłówek:** msclr\event.h

## <a name="begin_interface_map"></a><a name="begin_interface_map"></a>BEGIN_INTERFACE_MAP

Rozpoczyna definicję mapy interfejsu, gdy jest używana w pliku implementacji.

### <a name="syntax"></a>Składnia

```
BEGIN_INTERFACE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>Parametry

*klasa*<br/>
Klasa, w której ma być zdefiniowana mapa interfejsu

*Baseclass*<br/>
Klasa, z której pochodzi *klasa.*

### <a name="remarks"></a>Uwagi

Dla każdego interfejsu, który jest zaimplementowany, istnieje co najmniej jeden INTERFACE_PART wywołań makr. Dla każdego agregacji, który używa klasy, istnieje jeden INTERFACE_AGGREGATE wywołania makra.

Aby uzyskać więcej informacji na temat map interfejsu, zobacz [Uwaga techniczna 38](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="commandhandler-delegate"></a><a name="commandhandler"></a>Delegat CommandHandler

Rejestruje metody wywołania zwrotnego ze źródłem polecenia.

### <a name="syntax"></a>Składnia

```
delegate void CommandHandler(  UINT^ cmdID  );
```

### <a name="parameters"></a>Parametry

*identyfikator cmdID*<br/>
Identyfikator polecenia.

### <a name="remarks"></a>Uwagi

Ten delegat rejestruje metody wywołania zwrotnego ze źródłem polecenia. Po dodaniu pełnomocnika do obiektu źródłowego polecenia, metoda wywołania zwrotnego staje się program obsługi dla poleceń pochodzących z określonego źródła.

Aby uzyskać więcej informacji, zobacz [Jak: Dodawanie routingu poleceń do formantu Formularze systemu Windows](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md).

Aby uzyskać więcej informacji na temat korzystania z formularzy systemu Windows, zobacz [Korzystanie z formantu użytkownika formularza systemu Windows w programie MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwinforms.h (zdefiniowany w zestawie atlmfc\lib\mfcmifc80.dll)

## <a name="commanduihandler"></a><a name="commanduihandler"></a>CommandUIHandler (CommandUIHandler)

Rejestruje metody wywołania zwrotnego za pomocą komunikatu polecenia aktualizacji interfejsu użytkownika.

### <a name="syntax"></a>Składnia

```
delegate void CommandUIHandler(  unsigned int cmdID, ICommandUI^ cmdUI);
```

### <a name="parameters"></a>Parametry

*identyfikator cmdID*<br/>
Identyfikator polecenia.

*polecenie cmdUI*<br/>
Identyfikator komunikatu polecenia.

### <a name="remarks"></a>Uwagi

Ten delegat rejestruje metody wywołania zwrotnego za pomocą komunikatu polecenia aktualizacji interfejsu użytkownika. `CommandUIHandler`jest podobny do [CommandHandler,](#commandhandler) z tą różnicą, że ten delegat jest używany z poleceniami aktualizacji obiektu interfejsu użytkownika. Polecenia aktualizacji interfejsu użytkownika powinny być mapowane jeden do jednego z metod obsługi komunikatów.

Aby uzyskać więcej informacji na temat korzystania z formularzy systemu Windows, zobacz [Korzystanie z formantu użytkownika formularza systemu Windows w programie MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwinforms.h (zdefiniowany w zestawie atlmfc\lib\mfcmifc80.dll)

## <a name="end_delegate_map"></a><a name="end_delegate_map"></a>END_DELEGATE_MAP

Kończy mapę delegata.

### <a name="syntax"></a>Składnia

```
END_DELEGATE_MAP();
```

### <a name="remarks"></a>Uwagi

To makro oznacza koniec listy wpisów delegata, które tworzą mapę pełnomocnika. Na przykład, jak to makro jest używane, zobacz [EVENT_DELEGATE_ENTRY](#event_delegate_entry).

### <a name="requirements"></a>Wymagania

**Nagłówek:** msclr\event.h

## <a name="end_interface_map"></a><a name="end_interface_map"></a>END_INTERFACE_MAP

Kończy mapę interfejsu w pliku implementacji.

### <a name="syntax"></a>Składnia

```
END_INTERFACE_MAP( )
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat map interfejsu, zobacz [Uwaga techniczna 38](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="event_delegate_entry"></a><a name="event_delegate_entry"></a>EVENT_DELEGATE_ENTRY

Tworzy wpis na mapie pełnomocnika.

### <a name="syntax"></a>Składnia

```
EVENT_DELEGATE_ENTRY(MEMBER, ARG0, ARG1);
```

### <a name="parameters"></a>Parametry

*Członkowskich*<br/>
Metoda obsługi zdarzeń, która ma być dołączona do formantu.

*Arg0 (arg0)*<br/>
Pierwszy argument metody obsługi zdarzeń zarządzanych, na przykład `Object^`.

*Arg1 (arg1)*<br/>
Drugi argument metody obsługi zdarzeń zarządzanych, na przykład `EventArgs^`.

### <a name="remarks"></a>Uwagi

Każdy wpis na mapie pełnomocnika odpowiada delegatowi zarządzanego programu obsługi zdarzeń utworzonego przez [MAKE_DELEGATE](#make_delegate).

### <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje, jak używać EVENT_DELEGATE_ENTRY do tworzenia wpisu `OnClick` w mapie pełnomocnika dla programu obsługi zdarzeń; również zobacz przykład kodu w MAKE_DELEGATE. Aby uzyskać więcej informacji, zobacz [Jak: Sink Windows Forms Zdarzenia z natywnych klas C++.](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)

```cpp
BEGIN_DELEGATE_MAP(CMyView)
   EVENT_DELEGATE_ENTRY(OnClick, System::Object^, System::EventArgs^)
END_DELEGATE_MAP()
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** msclr\event.h

## <a name="interface_part"></a><a name="interface_part"></a>Interface_part

Używane między makro BEGIN_INTERFACE_MAP a makro END_INTERFACE_MAP dla każdego interfejsu, który będzie obsługiwał obiekt.

### <a name="syntax"></a>Składnia

```
INTERFACE_PART( theClass, iid, localClass)
```

### <a name="parameters"></a>Parametry

*klasa*<br/>
Nazwa klasy zawierającej mapę interfejsu.
*Iid*<br/>
Identyfikator, który ma być mapowany do klasy osadzonej.
*localClass (Klasa lokalna)*<br/>
Nazwa klasy lokalnej.

### <a name="remarks"></a>Uwagi

Umożliwia mapowanie identyfikatora do członka klasy wskazanej przez *klasę* i *localClass*.

Aby uzyskać więcej informacji na temat map interfejsu, zobacz [Uwaga techniczna 38](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

## <a name="make_delegate"></a><a name="make_delegate"></a>MAKE_DELEGATE

Dołącza program obsługi zdarzeń do formantu zarządzanego.

### <a name="syntax"></a>Składnia

```
MAKE_DELEGATE( DELEGATE,  MEMBER) ;
```

### <a name="parameters"></a>Parametry

*Delegata*<br/>
Typ delegata zarządzanego programu obsługi zdarzeń, takiego jak [EventHandler](/dotnet/api/system.eventhandler).

*Członkowskich*<br/>
Nazwa metody obsługi zdarzeń, która ma być dołączona do formantu.

### <a name="remarks"></a>Uwagi

To makro tworzy delegata programu obsługi zdarzeń zarządzanych typu *DELEGAT* i nazwy *MEMBER*. Delegat programu obsługi zdarzeń zarządzanych umożliwia klasie macierzystej do obsługi zdarzeń zarządzanych.

### <a name="example"></a>Przykład

W poniższym przykładzie `MAKE_DELEGATE` kodu pokazano, jak wywołać, aby dołączyć program obsługi `OnClick` zdarzeń do formantu `MyControl`MFC. Aby uzyskać szersze wyjaśnienie, jak to makro działa w aplikacji MFC, zobacz [Jak: Sink Windows Forms Zdarzenia z natywnych klas C++.](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)

```cpp
// CMyView derives from CWinFormsView.
void CMyView::OnInitialUpdate()
{
   CWinFormsView::OnInitialUpdate();

   GetControl()->Click += MAKE_DELEGATE(System::EventHandler, OnClick);
}
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** msclr\event.h

## <a name="see-also"></a>Zobacz też

[Instrukcje: wychwytywanie zdarzeń interfejsu Windows Forms z klas natywnych języka C++](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)<br/>
[Instrukcje: dodawanie routingu poleceń do formantu interfejsu Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[Makra i globals](mfc-macros-and-globals.md)<br/>
