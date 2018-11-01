---
title: Delegat i makra mapy interfejsu (MFC)
ms.date: 03/30/2017
helpviewer_keywords:
- delegate map macros [MFC]
- event map macros [MFC]
- interface map macros [MFC]
ms.assetid: 3840e642-ff7d-4bdc-998b-c7d8fc50890e
ms.openlocfilehash: 91bd50ca34893b7dd91f6402f5ca95865f872650
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429344"
---
|||
|-|-|
|[BEGIN_DELEGATE_MAP](#begin_delegate_map)|Rozpoczyna się mapa delegata.|
|[BEGIN_INTERFACE_MAP](#begin_interface_map)|Rozpoczyna się definicji podłączony mapy.|
|[Commandhandler — obiekt delegowany](#commandhandler)|Rejestruje metody wywołania zwrotnego z źródło polecenia.  |
|[END_DELEGATE_MAP](#end_delegate_map)|Kończy się mapa delegata.|
|[END_INTERFACE_MAP](#end_interface_map)|Kończy się mapę interfejsu w pliku implementacji. |
|[EVENT_DELEGATE_ENTRY](#event_delegate_entry)|Tworzy wpis w mapie delegata.|
|[INTERFACE_PART](#interface_part)|Używane między makro BEGIN_INTERFACE_MAP i END_INTERFACE_MAP — makro dla każdego interfejsu, który jaki obsługiwał będzie obiekt.|
|[MAKE_DELEGATE](#make_delegate)|Dołącza program obsługi zdarzeń do zarządzanego formantu.|

## <a name="begin_delegate_map"></a> BEGIN_DELEGATE_MAP

Rozpoczyna się mapa delegata.

### <a name="syntax"></a>Składnia

```
BEGIN_DELEGATE_MAP(  CLASS );
```

### <a name="parameters"></a>Parametry

*KLASA*<br/>
Klasa, w którym jest hostowana zarządzanego formantu.

### <a name="remarks"></a>Uwagi

To makro oznacza początek listy zapisów delegatów, które tworzą mapę delegata. Aby uzyskać przykład sposobu używania tego makra, zobacz [EVENT_DELEGATE_ENTRY](#event_delegate_entry).

### <a name="requirements"></a>Wymagania

**Nagłówek:** msclr\event.h

### <a name="see-also"></a>Zobacz też

[Instrukcje: wychwytywanie zdarzeń interfejsu Windows Forms z klas natywnych języka C++](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)

##  <a name="begin_interface_map"></a>BEGIN_INTERFACE_MAP

Rozpoczyna się definicji podłączony mapy, gdy są używane w pliku implementacji.

### <a name="syntax"></a>Składnia

```
BEGIN_INTERFACE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Klasy, w którym ma zostać określona mapy interfejsu

*baseClass*<br/>
Klasa, z której *theClass* pochodzi od klasy.

### <a name="remarks"></a>Uwagi

Dla każdego interfejsu, który jest implementowany jest jeden lub więcej wywołań makra INTERFACE_PART. Dla każdej agregacji, z której korzysta ta klasa jest jedno wywołanie makra INTERFACE_AGGREGATE.

Aby uzyskać więcej informacji na temat mapy interfejsu, zobacz [techniczne 38 Uwaga](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

##  <a name="commandhandler"></a>Commandhandler — obiekt delegowany

Rejestruje metody wywołania zwrotnego z źródło polecenia.

### <a name="syntax"></a>Składnia

```
delegate void CommandHandler(  UINT^ cmdID  );
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
Identyfikator polecenia.

### <a name="remarks"></a>Uwagi

Ten delegat rejestruje metody wywołania zwrotnego z źródło polecenia. Po dodaniu delegata do obiektu źródła polecenia, metody wywołania zwrotnego staje się procedury obsługi dla poleceń z określonego źródła.

Aby uzyskać więcej informacji, zobacz [porady: Dodawanie routingu poleceń do formantu programu Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md).

Aby uzyskać więcej informacji na temat korzystania z Windows Forms, zobacz [za pomocą kontrolki użytkownika formularza Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwinforms.h (zdefiniowany w zestawie atlmfc\lib\mfcmifc80.dll)

### <a name="see-also"></a>Zobacz też

[Instrukcje: dodawanie routingu poleceń do formantu interfejsu Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)

##  <a name="commanduihandler"></a>Commanduihandler — obiekt

Rejestruje metody wywołania zwrotnego z komunikatem polecenia aktualizacji interfejsu użytkownika.

### <a name="syntax"></a>Składnia

```
delegate void CommandUIHandler(  unsigned int cmdID, ICommandUI^ cmdUI);
```

### <a name="parameters"></a>Parametry

*cmdID*<br/>
Identyfikator polecenia.

*cmdUI*<br/>
Identyfikator polecenia komunikatu.

### <a name="remarks"></a>Uwagi

Ten delegat rejestruje metody wywołania zwrotnego z komunikatem polecenia aktualizacji interfejsu użytkownika. `CommandUIHandler` jest podobny do [commandhandler — obiekt](#commandhandler) z tą różnicą, że ten delegat jest używane z polecenia aktualizacji obiektu interfejsu użytkownika. Polecenia aktualizacji interfejsu użytkownika powinny mapowane w jeden do jednego z metody obsługi wiadomości.

Aby uzyskać więcej informacji na temat korzystania z Windows Forms, zobacz [za pomocą kontrolki użytkownika formularza Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwinforms.h (zdefiniowany w zestawie atlmfc\lib\mfcmifc80.dll)

### <a name="see-also"></a>Zobacz też

[Instrukcje: dodawanie routingu poleceń do formantu interfejsu Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[CommandHandler](#commandhandler)

##  <a name="end_delegate_map"></a>END_DELEGATE_MAP

Kończy się mapa delegata.

### <a name="syntax"></a>Składnia

```
END_DELEGATE_MAP();
```

### <a name="remarks"></a>Uwagi

To makro oznacza koniec listy wpisów delegata, które tworzą mapę delegata. Aby uzyskać przykład sposobu używania tego makra, zobacz [EVENT_DELEGATE_ENTRY](#event_delegate_entry).

### <a name="requirements"></a>Wymagania

**Nagłówek:** msclr\event.h

### <a name="see-also"></a>Zobacz też

[Instrukcje: wychwytywanie zdarzeń interfejsu Windows Forms z klas natywnych języka C++](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)

##  <a name="end_interface_map"></a>END_INTERFACE_MAP

Kończy się mapę interfejsu w pliku implementacji.

### <a name="syntax"></a>Składnia

```
END_INTERFACE_MAP( )
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji na temat mapy interfejsu zobacz [techniczne 38 Uwaga](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

### <a name="see-also"></a>Zobacz też

[Makra i funkcje globalne](mfc-macros-and-globals.md)<br/>
[BEGIN_INTERFACE_MAP](#begin_interface_map)

##  <a name="event_delegate_entry"></a>EVENT_DELEGATE_ENTRY

Tworzy wpis w mapie delegata.

### <a name="syntax"></a>Składnia

```
EVENT_DELEGATE_ENTRY(MEMBER, ARG0, ARG1);
```

### <a name="parameters"></a>Parametry

*ELEMENT CZŁONKOWSKI*<br/>
Metoda obsługi zdarzeń do dołączenia do kontrolki.

*ARG0*<br/>
Pierwszy argument metody obsługi zdarzeń zarządzanych, takich jak `Object^`.

*ARG1*<br/>
Drugi argument metody obsługi zdarzeń zarządzanych, takich jak `EventArgs^`.

### <a name="remarks"></a>Uwagi

Każdy wpis w mapie delegata odnosi się do delegata obsługi zdarzeń zarządzanych, utworzone przez [MAKE_DELEGATE](#make_delegate).

### <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje jak utworzyć wpis w mapowaniu delegata dla za pomocą EVENT_DELEGATE_ENTRY `OnClick` programu obsługi zdarzeń; a także zobacz przykładowy kod z MAKE_DELEGATE. Aby uzyskać więcej informacji, zobacz [jak: ujścia zdarzeń interfejsu Windows Forms z klas natywnych języka C++](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md).

```cpp
BEGIN_DELEGATE_MAP(CMyView)
   EVENT_DELEGATE_ENTRY(OnClick, System::Object^, System::EventArgs^)
END_DELEGATE_MAP()

```

### <a name="requirements"></a>Wymagania

**Nagłówek:** msclr\event.h

### <a name="see-also"></a>Zobacz też

[MAKE_DELEGATE](#make_delegate)<br/>
[BEGIN_DELEGATE_MAP](#begin_delegate_map)<br/>
[END_DELEGATE_MAP](#end_delegate_map)

##  <a name="interface_part"></a>INTERFACE_PART

Używane między makro BEGIN_INTERFACE_MAP i END_INTERFACE_MAP — makro dla każdego interfejsu, który jaki obsługiwał będzie obiekt.

### <a name="syntax"></a>Składnia

```
INTERFACE_PART( theClass, iid, localClass)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Nazwa klasy, która zawiera mapę interfejsu.
*IID*<br/>
Identyfikatora IID, który ma być mapowane na klasie osadzonej.
*localClass*<br/>
Nazwa klasy lokalnej.

### <a name="remarks"></a>Uwagi

Umożliwia mapowania identyfikatora IID do elementu członkowskiego klasy wskazanego przez *theClass* i *localClass*.

Aby uzyskać więcej informacji na temat mapy interfejsu, zobacz [techniczne 38 Uwaga](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** afxwin.h

##  <a name="make_delegate"></a>MAKE_DELEGATE

Dołącza program obsługi zdarzeń do zarządzanego formantu.

### <a name="syntax"></a>Składnia

```
MAKE_DELEGATE( DELEGATE,  MEMBER) ;
```

### <a name="parameters"></a>Parametry

*DELEGAT*<br/>
Typem obsługi zdarzeń zarządzanych delegować, takich jak [EventHandler](assetId:///T:System.EventHandler?qualifyHint=False&autoUpgrade=True).

*ELEMENT CZŁONKOWSKI*<br/>
Nazwa metody obsługi zdarzeń do dołączenia do kontrolki.

### <a name="remarks"></a>Uwagi

To makro tworzy delegata obsługi zdarzeń zarządzanego typu *DELEGOWAĆ* i nazwy *elementu członkowskiego*. Delegata obsługi zdarzeń zarządzanych umożliwia klasy natywnej do obsługi zdarzeń zarządzanych.

### <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje sposób wywoływania `MAKE_DELEGATE` można dołączyć `OnClick` procedurę obsługi zdarzeń do kontrolki MFC `MyControl`. Szerszy wyjaśnienie sposobu działania tego makra w aplikacji MFC, zobacz [jak: ujścia zdarzeń interfejsu Windows Forms z klas natywnych języka C++](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md).

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

### <a name="see-also"></a>Zobacz też

[BEGIN_DELEGATE_MAP](#begin_delegate_map)<br/>
[END_DELEGATE_MAP](#end_delegate_map)<br/>
[EVENT_DELEGATE_ENTRY](#event_delegate_entry)

