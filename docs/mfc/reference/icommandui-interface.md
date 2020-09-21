---
title: ICommandUI, interfejs
ms.date: 09/07/2019
f1_keywords:
- ICommandUI
- AFXWINFORMS/ICommandUI
- AFXWINFORMS/icommandui__Check
- AFXWINFORMS/ICommandUI::ContinueRouting
- AFXWINFORMS/ICommandUI::Enabled
- AFXWINFORMS/ICommandUI::ID
- AFXWINFORMS/ICommandUI::Index
- AFXWINFORMS/ICommandUI::Radio
- AFXWINFORMS/ICommandUI::Text
helpviewer_keywords:
- ICommandUI interface [MFC]
ms.assetid: 134afe8d-dcdf-47ca-857a-a166a6b665dd
ms.openlocfilehash: 0c185e873f526403e86cb5a80f6e0631f8654284
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743441"
---
# <a name="icommandui-interface"></a>ICommandUI, interfejs

Zarządza poleceniami interfejsu użytkownika.

## <a name="syntax"></a>Składnia

```
interface class ICommandUI
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[icommandui__Check](#check)|Ustawia element interfejsu użytkownika dla tego polecenia do odpowiedniego stanu sprawdzania.|
|[ICommandUI::ContinueRouting](#continuerouting)|Informuje mechanizm routingu poleceń, aby kontynuować kierowanie bieżącego komunikatu do łańcucha programów obsługi.|
|[ICommandUI:: Enabled](#enabled)|Włącza lub wyłącza element interfejsu użytkownika dla tego polecenia.|
|[ICommandUI:: ID](#id)|Pobiera identyfikator obiektu interfejsu użytkownika reprezentowanego przez `ICommandUI` obiekt.|
|[ICommandUI:: index](#index)|Pobiera indeks obiektu interfejsu użytkownika reprezentowanego przez `ICommandUI` obiekt.|
|[ICommandUI:: Radio](#radio)|Ustawia element interfejsu użytkownika dla tego polecenia do odpowiedniego stanu sprawdzania.|
|[ICommandUI:: text](#text)|Ustawia tekst elementu interfejsu użytkownika dla tego polecenia.|

### <a name="remarks"></a>Uwagi

Ten interfejs zapewnia metody i właściwości, które zarządzają poleceniami interfejsu użytkownika. `ICommandUI` jest podobna do [klasy CCmdUI](../../mfc/reference/ccmdui-class.md), z tą różnicą, że `ICommandUI` jest używana dla aplikacji MFC, które współdziałają ze składnikami platformy .NET.

`ICommandUI` jest używany w ramach procedury obsługi ON_UPDATE_COMMAND_UI w klasie pochodnej [ICommandTarget](../../mfc/reference/icommandtarget-interface.md). Gdy użytkownik uaktywnia (wybiera lub klika) menu, każdy element menu jest wyświetlany jako włączony lub wyłączony. Obiekt docelowy każdego polecenia menu dostarcza te informacje poprzez implementację procedury obsługi ON_UPDATE_COMMAND_UI. Dla każdego z poleceń obiektów interfejsu użytkownika w aplikacji użyj [kreatora klas](mfc-class-wizard.md) , aby utworzyć wpis mapy komunikatów i prototyp funkcji dla każdej procedury obsługi.

Aby uzyskać więcej informacji na temat sposobu `ICommandUI` użycia interfejsu w routingu poleceń, zobacz [How to: Add Command Routing to the Windows Forms Control](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md).

Aby uzyskać więcej informacji na temat korzystania z Windows Forms, zobacz [Korzystanie z kontrolki użytkownika formularza systemu Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

Aby uzyskać więcej informacji na temat sposobu zarządzania poleceniami interfejsu użytkownika w MFC, zobacz [CCmdUI Class](../../mfc/reference/ccmdui-class.md).

## <a name="icommanduicheck"></a><a name="check"></a> ICommandUI:: Check

Ustawia element interfejsu użytkownika dla tego polecenia do odpowiedniego stanu sprawdzania.

```
property UICheckState Check;
```

### <a name="remarks"></a>Uwagi

Ta właściwość ustawia element interfejsu użytkownika dla tego polecenia do odpowiedniego stanu sprawdzania. Ustaw opcję Sprawdź następujące wartości:

- 0 — Usuń zaznaczenie
- 1 sprawdzenie
- 2 Ustaw nieokreślony

## <a name="icommanduicontinuerouting"></a><a name="continuerouting"></a> ICommandUI::ContinueRouting

Informuje mechanizm routingu poleceń, aby kontynuować kierowanie bieżącego komunikatu do łańcucha programów obsługi.

```cpp
void ContinueRouting();
```

### <a name="remarks"></a>Uwagi

Jest to zaawansowana funkcja członkowska, która powinna być używana w połączeniu z obsługą ON_COMMAND_EX, która zwraca wartość FALSE. Aby uzyskać więcej informacji, zobacz Uwagi techniczne TN006: mapy komunikatów.

## <a name="icommanduienabled"></a><a name="enabled"></a> ICommandUI:: Enabled

Włącza lub wyłącza element interfejsu użytkownika dla tego polecenia.

```
property bool Enabled;
```

### <a name="remarks"></a>Uwagi

Ta właściwość włącza lub wyłącza element interfejsu użytkownika dla tego polecenia. Ustaw wartość TRUE, aby włączyć element, FALSE, aby go wyłączyć.

## <a name="icommanduiid"></a><a name="id"></a> ICommandUI:: ID

Pobiera identyfikator obiektu interfejsu użytkownika reprezentowanego przez obiekt ICommandUI.

```
property unsigned int ID;
```

### <a name="remarks"></a>Uwagi

Ta właściwość pobiera identyfikator (uchwyt) elementu menu, przycisku paska narzędzi lub innego obiektu interfejsu użytkownika reprezentowanego przez obiekt ICommandUI.

## <a name="icommanduiindex"></a><a name="index"></a> ICommandUI:: index

Pobiera indeks obiektu interfejsu użytkownika reprezentowanego przez obiekt ICommandUI.

```
property unsigned int Index;
```

### <a name="remarks"></a>Uwagi

Ta właściwość Pobiera indeks (uchwyt) elementu menu, przycisku paska narzędzi lub innego obiektu interfejsu użytkownika reprezentowanego przez obiekt ICommandUI.

## <a name="icommanduiradio"></a><a name="radio"></a> ICommandUI:: Radio

Ustawia element interfejsu użytkownika dla tego polecenia do odpowiedniego stanu sprawdzania.

```
property bool Radio;
```

### <a name="remarks"></a>Uwagi

Ta właściwość ustawia element interfejsu użytkownika dla tego polecenia do odpowiedniego stanu sprawdzania. Ustaw dla opcji Radio wartość TRUE, aby włączyć element; w przeciwnym razie FALSE.

## <a name="icommanduitext"></a><a name="text"></a> ICommandUI:: text

Ustawia tekst elementu interfejsu użytkownika dla tego polecenia.

```
property String^ Text;
```

### <a name="remarks"></a>Uwagi

Ta właściwość ustawia tekst elementu interfejsu użytkownika dla tego polecenia. Ustaw tekst jako uchwyt ciągu tekstowego.

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwinforms. h (zdefiniowany w zestawie atlmfc\lib\mfcmifc80.dll)

## <a name="see-also"></a>Zobacz też

[Klasa CCmdUI](../../mfc/reference/ccmdui-class.md)
