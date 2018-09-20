---
title: Klasa Icommandui | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- ICommandUI interface [MFC]
ms.assetid: 134afe8d-dcdf-47ca-857a-a166a6b665dd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7ec76a554068dbec050078a0e0558cecd583410c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429213"
---
# <a name="icommandui-interface"></a>Klasa Icommandui

Zarządza poleceń interfejsu użytkownika.

## <a name="syntax"></a>Składnia

```
interface class ICommandUI
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[icommandui__Check](#check)|Ustawia stan zaznaczenia odpowiednich element interfejsu użytkownika dla tego polecenia.|
|[ICommandUI::ContinueRouting](#continuerouting)|Informuje mechanizm routingu poleceń, aby kontynuować, routing do bieżącej wiadomości w łańcuchu obsługi.|
|[ICommandUI::Enabled](#enabled)|Włącza lub wyłącza element interfejsu użytkownika dla tego polecenia.|
|[ICommandUI::ID](#id)|Pobiera identyfikator obiektu interfejsu użytkownika, które są reprezentowane przez `ICommandUI` obiektu.|
|[ICommandUI::Index](#index)|Pobiera indeks obiektu interfejsu użytkownika, które są reprezentowane przez `ICommandUI` obiektu.|
|[ICommandUI::Radio](#radio)|Ustawia stan zaznaczenia odpowiednich element interfejsu użytkownika dla tego polecenia.|
|[ICommandUI::Text](#text)|Ustawia tekst elementu interfejsu użytkownika dla tego polecenia.|

## <a name="remarks"></a>Uwagi

Ten interfejs zapewnia metody i właściwości, które zarządzają poleceń interfejsu użytkownika. `ICommandUI` jest podobny do [klasa CCmdUI](../../mfc/reference/ccmdui-class.md), chyba że `ICommandUI` jest używana dla aplikacji MFC, które współpracować ze składnikami platformy .NET.

`ICommandUI` jest używana wewnątrz procedury obsługi ON_UPDATE_COMMAND_UI w [obiektu ICommandTarget](../../mfc/reference/icommandtarget-interface.md)-klasy pochodnej. Gdy użytkownik aplikacji aktywuje (zaznacza lub kliknięcia) menu, każdy element menu jest wyświetlany jako włączone lub wyłączone. Celem każdego polecenia menu udostępnia te informacje poprzez implementację programu obsługi ON_UPDATE_COMMAND_UI. Dla każdego z obiektów interfejsu użytkownika poleceń w aplikacji okno właściwości do utworzenia wpisu mapy wiadomości i prototypu funkcji dla każdej procedury obsługi.

Aby uzyskać więcej informacji na temat sposobu `ICommandUI` interfejs jest używany w routingu poleceń, zobacz [porady: Dodawanie routingu poleceń do formantu programu Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md).

Aby uzyskać więcej informacji na temat korzystania z Windows Forms, zobacz [za pomocą kontrolki użytkownika formularza Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

Aby uzyskać więcej informacji na temat sposobu zarządzania poleceń interfejsu użytkownika w MFC, zobacz [klasa CCmdUI](../../mfc/reference/ccmdui-class.md).

## <a name="check"></a> ICommandUI::Check

Ustawia stan zaznaczenia odpowiednich element interfejsu użytkownika dla tego polecenia.
```
property UICheckState Check;
```
## <a name="remarks"></a>Uwagi

Ta właściwość ustawia element interfejsu użytkownika dla tego polecenia stanie odpowiedniej kontroli. Sprawdź, ustaw następujące wartości:
- Usuń zaznaczenie 0
- Sprawdzanie 1
- Ustaw nieokreślony 2

## <a name="continuerouting"></a> ICommandUI::ContinueRouting

Informuje mechanizm routingu polecenia nadal routingu do bieżącej wiadomości w łańcuchu programów obsługi.
```
void ContinueRouting();
```
## <a name="remarks"></a>Uwagi

Jest to funkcja członków na poziomie zaawansowanym, który ma zostać użyty w połączeniu z programem obsługi ON_COMMAND_EX, która zwraca wartość FALSE. Aby uzyskać więcej informacji, zobacz techniczne Uwaga TN006: mapy komunikatów.

## <a name="enabled"></a> ICommandUI::Enabled

Włącza lub wyłącza element interfejsu użytkownika dla tego polecenia.
```
property bool Enabled;
```
## <a name="remarks"></a>Uwagi

Tej właściwości Włącza lub wyłącza element interfejsu użytkownika dla tego polecenia. Włączone, aby należy ustawić wartość TRUE powoduje włączenie elementu wartość FALSE, aby je wyłączyć.

## <a name="id"></a> ICommandUI::ID

Pobiera identyfikator obiektu interfejsu użytkownika, które są reprezentowane przez obiekt ICommandUI.
```
property unsigned int ID;
```
## <a name="remarks"></a>Uwagi

Tej właściwości pobiera identyfikator (uchwyt) elementu menu, przycisk paska narzędzi lub inny obiekt interfejsu użytkownika, reprezentowane przez obiekt ICommandUI.

## <a name="index"></a> ICommandUI::Index

Pobiera indeks obiektu interfejsu użytkownika, które są reprezentowane przez obiekt ICommandUI.
```
property unsigned int Index;
```
## <a name="remarks"></a>Uwagi

Tej właściwości pobiera indeks (uchwyt) elementu menu, przycisk paska narzędzi lub inny obiekt interfejsu użytkownika, reprezentowane przez obiekt ICommandUI.

## <a name="radio"></a> ICommandUI::Radio

Ustawia stan zaznaczenia odpowiednich element interfejsu użytkownika dla tego polecenia.
```
property bool Radio;
```
## <a name="remarks"></a>Uwagi

Ta właściwość ustawia element interfejsu użytkownika dla tego polecenia stanie odpowiedniej kontroli. Ustaw opcji na wartość TRUE powoduje włączenie elementu; w przeciwnym razie wartość FALSE.

## <a name="text"></a> ICommandUI::Text

Ustawia tekst elementu interfejsu użytkownika dla tego polecenia.
```
property String^ Text;
```
## <a name="remarks"></a>Uwagi

Ta właściwość określa tekst elementu interfejsu użytkownika dla tego polecenia. Ustaw tekst do uchwytu ciągu tekstowego.

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwinforms.h (zdefiniowany w zestawie atlmfc\lib\mfcmifc80.dll)

## <a name="see-also"></a>Zobacz też

[Klasa CCmdUI](../../mfc/reference/ccmdui-class.md)
