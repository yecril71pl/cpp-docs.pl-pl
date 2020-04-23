---
title: Klasa ICommandUI
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
ms.openlocfilehash: b75509beb7287fad5e51dc9d15fc3e47cacf6854
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751311"
---
# <a name="icommandui-interface"></a>Klasa ICommandUI

Zarządza poleceniami interfejsu użytkownika.

## <a name="syntax"></a>Składnia

```
interface class ICommandUI
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[icommandui__Check](#check)|Ustawia element interfejsu użytkownika dla tego polecenia na odpowiedni stan sprawdzania.|
|[ICommandUI::ContinueRouting](#continuerouting)|Informuje mechanizm routingu poleceń, aby kontynuować routing bieżącej wiadomości w dół łańcucha obsługi.|
|[ICommandUI::Włączone](#enabled)|Włącza lub wyłącza element interfejsu użytkownika dla tego polecenia.|
|[ICommandUI::ID](#id)|Pobiera identyfikator obiektu interfejsu użytkownika reprezentowanego `ICommandUI` przez obiekt.|
|[ICommandUI::Indeks](#index)|Pobiera indeks obiektu interfejsu użytkownika reprezentowanego `ICommandUI` przez obiekt.|
|[ICommandUI::Radio](#radio)|Ustawia element interfejsu użytkownika dla tego polecenia na odpowiedni stan sprawdzania.|
|[ICommandUI::Tekst](#text)|Ustawia tekst elementu interfejsu użytkownika dla tego polecenia.|

## <a name="remarks"></a>Uwagi

Ten interfejs zawiera metody i właściwości, które zarządzają poleceniami interfejsu użytkownika. `ICommandUI`jest podobny do [klasy CCmdUI](../../mfc/reference/ccmdui-class.md), z tą różnicą, że `ICommandUI` jest używany dla aplikacji MFC, które współdziałają ze składnikami .NET.

`ICommandUI`jest używany w programie obsługi ON_UPDATE_COMMAND_UI w klasie pochodnej [ICommandTarget.](../../mfc/reference/icommandtarget-interface.md) Gdy użytkownik aplikacji aktywuje (wybiera lub klika) menu, każdy element menu jest wyświetlany jako włączony lub wyłączony. Miejsce docelowe każdego polecenia menu zawiera te informacje, implementując program obsługi ON_UPDATE_COMMAND_UI. Dla każdego z obiektów interfejsu użytkownika polecenia w aplikacji, użyj [Kreatora klas,](mfc-class-wizard.md) aby utworzyć wpis mapy wiadomości i prototyp funkcji dla każdego programu obsługi.

Aby uzyskać więcej `ICommandUI` informacji na temat sposobu wykorzystania interfejsu w routingu poleceń, zobacz [Jak: Dodawanie routingu poleceń do formantu Formularze systemu Windows](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md).

Aby uzyskać więcej informacji na temat korzystania z formularzy systemu Windows, zobacz [Korzystanie z formantu użytkownika formularza systemu Windows w programie MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

Aby uzyskać więcej informacji na temat zarządzania poleceniami interfejsu użytkownika w MFC, zobacz [Klasa CCmdUI](../../mfc/reference/ccmdui-class.md).

## <a name="icommanduicheck"></a><a name="check"></a>ICommandUI::Sprawdź

Ustawia element interfejsu użytkownika dla tego polecenia na odpowiedni stan sprawdzania.

```
property UICheckState Check;
```

## <a name="remarks"></a>Uwagi

Ta właściwość ustawia element interfejsu użytkownika dla tego polecenia do odpowiedniego stanu wyboru. Ustaw wartość Sprawdź na następujące wartości:

- 0 Odznacz zaznaczenie
- 1 Sprawdź
- 2 Nieokreślony zestaw

## <a name="icommanduicontinuerouting"></a><a name="continuerouting"></a>ICommandUI::ContinueRouting

Informuje mechanizm routingu polecenia, aby kontynuować routing bieżącej wiadomości w dół łańcucha obsługi.

```cpp
void ContinueRouting();
```

## <a name="remarks"></a>Uwagi

Jest to funkcja zaawansowanego elementu członkowskiego, która powinna być używana w połączeniu z ON_COMMAND_EX program obsługi, który zwraca FALSE. Aby uzyskać więcej informacji, zobacz Uwaga techniczna TN006: Mapy wiadomości.

## <a name="icommanduienabled"></a><a name="enabled"></a>ICommandUI::Włączone

Włącza lub wyłącza element interfejsu użytkownika dla tego polecenia.

```
property bool Enabled;
```

## <a name="remarks"></a>Uwagi

Ta właściwość włącza lub wyłącza element interfejsu użytkownika dla tego polecenia. Ustaw włącz wartość TRUE, aby włączyć element FALSE, aby go wyłączyć.

## <a name="icommanduiid"></a><a name="id"></a>ICommandUI::ID

Pobiera identyfikator obiektu interfejsu użytkownika reprezentowanego przez obiekt ICommandUI.

```
property unsigned int ID;
```

## <a name="remarks"></a>Uwagi

Ta właściwość pobiera identyfikator (uchwyt) elementu menu, przycisk paska narzędzi lub inny obiekt interfejsu użytkownika reprezentowane przez ICommandUI obiektu.

## <a name="icommanduiindex"></a><a name="index"></a>ICommandUI::Indeks

Pobiera indeks obiektu interfejsu użytkownika reprezentowanego przez obiekt ICommandUI.

```
property unsigned int Index;
```

## <a name="remarks"></a>Uwagi

Ta właściwość pobiera indeks (uchwyt) elementu menu, przycisk paska narzędzi lub inny obiekt interfejsu użytkownika reprezentowane przez ICommandUI obiektu.

## <a name="icommanduiradio"></a><a name="radio"></a>ICommandUI::Radio

Ustawia element interfejsu użytkownika dla tego polecenia na odpowiedni stan sprawdzania.

```
property bool Radio;
```

## <a name="remarks"></a>Uwagi

Ta właściwość ustawia element interfejsu użytkownika dla tego polecenia do odpowiedniego stanu wyboru. Ustaw wartość TRUE radia, aby włączyć element; w przeciwnym razie FALSE.

## <a name="icommanduitext"></a><a name="text"></a>ICommandUI::Tekst

Ustawia tekst elementu interfejsu użytkownika dla tego polecenia.

```
property String^ Text;
```

## <a name="remarks"></a>Uwagi

Ta właściwość ustawia tekst elementu interfejsu użytkownika dla tego polecenia. Ustaw tekst na uchwyt ciągu tekstowego.

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwinforms.h (zdefiniowany w zestawie atlmfc\lib\mfcmifc80.dll)

## <a name="see-also"></a>Zobacz też

[Klasa CCmdUI](../../mfc/reference/ccmdui-class.md)
