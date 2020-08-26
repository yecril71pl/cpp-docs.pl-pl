---
title: Makra delegata i mapy interfejsu (MFC)
ms.date: 03/30/2017
helpviewer_keywords:
- delegate map macros [MFC]
- event map macros [MFC]
- interface map macros [MFC]
ms.assetid: 3840e642-ff7d-4bdc-998b-c7d8fc50890e
ms.openlocfilehash: 01f5cbfb1f751823d218761410bc9091b73cb0a3
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837453"
---
# <a name="delegate-and-interface-map-macros"></a>Makra delegata i mapy interfejsu

MFC obsługuje te makra dla delegatów i map interfejsów:

|Nazwa|Opis|
|-|-|
|[BEGIN_DELEGATE_MAP](#begin_delegate_map)|Rozpoczyna mapę delegatów.|
|[BEGIN_INTERFACE_MAP](#begin_interface_map)|Rozpoczyna definicję mapy interfejsu.|
|[Delegat CommandHandler — obiekt](#commandhandler)|Rejestruje metody wywołania zwrotnego za pomocą źródła poleceń.  |
|[END_DELEGATE_MAP](#end_delegate_map)|Zamyka mapę delegatów.|
|[END_INTERFACE_MAP](#end_interface_map)|Zamyka mapę interfejsu w pliku implementacji. |
|[EVENT_DELEGATE_ENTRY](#event_delegate_entry)|Tworzy wpis w mapie delegatów.|
|[INTERFACE_PART](#interface_part)|Używany między makrem BEGIN_INTERFACE_MAP a makrom END_INTERFACE_MAP dla każdego interfejsu, który będzie obsługiwany przez obiekt.|
|[MAKE_DELEGATE](#make_delegate)|Dołącza procedurę obsługi zdarzeń do zarządzanego formantu.|

## <a name="begin_delegate_map"></a><a name="begin_delegate_map"></a> BEGIN_DELEGATE_MAP

Rozpoczyna mapę delegatów.

### <a name="syntax"></a>Składnia

```
BEGIN_DELEGATE_MAP(  CLASS );
```

### <a name="parameters"></a>Parametry

*OKREŚLONEJ*<br/>
Klasa, w której jest hostowany zarządzany formant.

### <a name="remarks"></a>Uwagi

To makro oznacza początek listy wpisów delegatów, które tworzą mapę delegatów. Aby zapoznać się z przykładem tego, jak to makro jest używane, zobacz [EVENT_DELEGATE_ENTRY](#event_delegate_entry).

### <a name="requirements"></a>Wymagania

**Nagłówek:** msclr\event.h

## <a name="begin_interface_map"></a><a name="begin_interface_map"></a> BEGIN_INTERFACE_MAP

Rozpoczyna definicję mapy interfejsu, gdy jest używana w pliku implementacji.

### <a name="syntax"></a>Składnia

```
BEGIN_INTERFACE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Klasa, w której ma zostać zdefiniowana Mapa interfejsu

*baseClass*<br/>
Klasa, z której pochodzi *theClass* .

### <a name="remarks"></a>Uwagi

Dla każdego wdrożonego interfejsu istnieje co najmniej jedno INTERFACE_PART wywołanie makra. Dla każdej wartości zagregowanej używanej przez klasę istnieje jedno INTERFACE_AGGREGATE wywołanie makra.

Aby uzyskać więcej informacji na temat map interfejsów, zobacz [Uwaga techniczna 38](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

## <a name="commandhandler-delegate"></a><a name="commandhandler"></a> Delegat CommandHandler — obiekt

Rejestruje metody wywołania zwrotnego za pomocą źródła poleceń.

### <a name="syntax"></a>Składnia

```
delegate void CommandHandler(  UINT^ cmdID  );
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
Identyfikator polecenia.

### <a name="remarks"></a>Uwagi

Ten delegat rejestruje metody wywołania zwrotnego ze źródłem poleceń. Po dodaniu delegata do obiektu źródłowego polecenia Metoda wywołania zwrotnego zmienia się w procedurę obsługi poleceń pochodzących z określonego źródła.

Aby uzyskać więcej informacji, zobacz [jak: Dodawanie poleceń routingu do kontrolki Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md).

Aby uzyskać więcej informacji na temat korzystania z Windows Forms, zobacz [Korzystanie z kontrolki użytkownika formularza systemu Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwinforms. h (zdefiniowany w zestawie atlmfc\lib\mfcmifc80.dll)

## <a name="commanduihandler"></a><a name="commanduihandler"></a> Commanduihandler —

Rejestruje metody wywołania zwrotnego za pomocą komunikatu polecenia aktualizacji interfejsu użytkownika.

### <a name="syntax"></a>Składnia

```
delegate void CommandUIHandler(  unsigned int cmdID, ICommandUI^ cmdUI);
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
Identyfikator polecenia.

*cmdUI*<br/>
Identyfikator komunikatu polecenia.

### <a name="remarks"></a>Uwagi

Ten delegat rejestruje metody wywołania zwrotnego za pomocą komunikatu polecenia aktualizacji interfejsu użytkownika. `CommandUIHandler` jest podobny do [CommandHandler — obiekt](#commandhandler) , z tą różnicą, że ten delegat jest używany z poleceniami aktualizacji obiektu interfejsu użytkownika. Polecenia aktualizacji interfejsu użytkownika powinny być mapowane jeden do jednego z metodami obsługi komunikatów.

Aby uzyskać więcej informacji na temat korzystania z Windows Forms, zobacz [Korzystanie z kontrolki użytkownika formularza systemu Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwinforms. h (zdefiniowany w zestawie atlmfc\lib\mfcmifc80.dll)

## <a name="end_delegate_map"></a><a name="end_delegate_map"></a> END_DELEGATE_MAP

Zamyka mapę delegatów.

### <a name="syntax"></a>Składnia

```
END_DELEGATE_MAP();
```

### <a name="remarks"></a>Uwagi

To makro oznacza koniec listy wpisów delegatów, które tworzą mapę delegatów. Aby zapoznać się z przykładem tego, jak to makro jest używane, zobacz [EVENT_DELEGATE_ENTRY](#event_delegate_entry).

### <a name="requirements"></a>Wymagania

**Nagłówek:** msclr\event.h

## <a name="end_interface_map"></a><a name="end_interface_map"></a> END_INTERFACE_MAP

Zamyka mapę interfejsu w pliku implementacji.

### <a name="syntax"></a>Składnia

```
END_INTERFACE_MAP( )
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat map interfejsów, zobacz [Uwaga techniczna 38](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

## <a name="event_delegate_entry"></a><a name="event_delegate_entry"></a> EVENT_DELEGATE_ENTRY

Tworzy wpis w mapie delegatów.

### <a name="syntax"></a>Składnia

```
EVENT_DELEGATE_ENTRY(MEMBER, ARG0, ARG1);
```

### <a name="parameters"></a>Parametry

*CZŁONKIEM*<br/>
Metoda obsługi zdarzeń, która ma zostać dołączona do kontrolki.

*ARG0*<br/>
Pierwszy argument metody obsługi zdarzeń zarządzanych, takich jak `Object^` .

*ARG1*<br/>
Drugi argument metody obsługi zdarzeń zarządzanych, takich jak `EventArgs^` .

### <a name="remarks"></a>Uwagi

Każdy wpis na mapie delegatów odnosi się do zarządzanego delegata obsługi zdarzeń utworzonego przez [MAKE_DELEGATE](#make_delegate).

### <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje, jak za pomocą EVENT_DELEGATE_ENTRY utworzyć wpis w mapie delegatów dla `OnClick` programu obsługi zdarzeń; Zobacz również przykład kodu w MAKE_DELEGATE. Aby uzyskać więcej informacji, zobacz [How to: ujścia Windows Forms Events z natywnych klas języka C++](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md).

```cpp
BEGIN_DELEGATE_MAP(CMyView)
   EVENT_DELEGATE_ENTRY(OnClick, System::Object^, System::EventArgs^)
END_DELEGATE_MAP()
```

### <a name="requirements"></a>Wymagania

**Nagłówek:** msclr\event.h

## <a name="interface_part"></a><a name="interface_part"></a> INTERFACE_PART

Używany między makrem BEGIN_INTERFACE_MAP a makrom END_INTERFACE_MAP dla każdego interfejsu, który będzie obsługiwany przez obiekt.

### <a name="syntax"></a>Składnia

```
INTERFACE_PART( theClass, iid, localClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Nazwa klasy, która zawiera mapę interfejsu.
*IID*<br/>
Identyfikator IID, który ma zostać zmapowany na osadzoną klasę.
*localClass*<br/>
Nazwa klasy lokalnej.

### <a name="remarks"></a>Uwagi

Umożliwia mapowanie identyfikatora IID do elementu członkowskiego klasy wskazywanej przez *theClass* i *localClass*.

Aby uzyskać więcej informacji na temat map interfejsów, zobacz [Uwaga techniczna 38](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin. h

## <a name="make_delegate"></a><a name="make_delegate"></a> MAKE_DELEGATE

Dołącza procedurę obsługi zdarzeń do zarządzanego formantu.

### <a name="syntax"></a>Składnia

```
MAKE_DELEGATE( DELEGATE,  MEMBER) ;
```

### <a name="parameters"></a>Parametry

*Wierz*<br/>
Typ delegata programu obsługi zdarzeń zarządzanych, taki jak [EventHandler](/dotnet/api/system.eventhandler).

*CZŁONKIEM*<br/>
Nazwa metody obsługi zdarzeń, która ma zostać dołączona do kontrolki.

### <a name="remarks"></a>Uwagi

To makro tworzy delegata programu obsługi zdarzeń zarządzanych typu *delegata* i nazwanego *elementu członkowskiego*. Delegat zarządzanego programu obsługi zdarzeń pozwala natywnej klasie obsługiwać zdarzenia zarządzane.

### <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje, jak wywołać, `MAKE_DELEGATE` Aby dołączyć `OnClick` procedurę obsługi zdarzeń do kontrolki MFC `MyControl` . Aby uzyskać szersze wyjaśnienie tego, jak to makro działa w aplikacji MFC, zobacz [How to: ujścia Windows Forms Events z natywnych klas języka C++](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md).

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

[Instrukcje: ujścia zdarzeń Windows Forms z natywnych klas języka C++](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)<br/>
[Instrukcje: Dodawanie routingu poleceń do kontrolki Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[Makra i Globals](mfc-macros-and-globals.md)<br/>
