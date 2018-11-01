---
title: Domyślne zdarzenia kontroli
ms.date: 11/04/2016
helpviewer_keywords:
- Dialog Editor [C++], default control events
- controls [C++], default control events
- events [C++], controls
- dialog box controls [C++], events
ms.assetid: 75556b23-18f5-4390-97a4-2ecad3309741
ms.openlocfilehash: 8cd0102be240bc98cf7900653b8fbb714e2a99a1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50520411"
---
# <a name="default-control-events"></a>Domyślne zdarzenia kontroli

Następujące nazwy kontrolki mają towarzyszący domyślne zdarzenia:

|Nazwa kontrolki|Domyślne zdarzenia|
|------------------|-------------------|
|Animowanie|ACN_START|
|Pole wyboru|BN_CLICKED|
|Pole kombi|CBN_SELCHANGE|
|Niestandardowe|TTN_GETDISPINFO|
|Wybór daty i godziny|DTN_DATETIMECHANGE —|
|Pole edycji|EN_CHANGE|
|Pole grupy|(Nie dotyczy)|
|Klawisz skrótu|NM_OUTOFMEMORY —|
|Adres IP|IPN_FIELDCHANGED|
|Lista|LVN_ITEMCHANGE|
|Pole listy|LBN_SELCHANGE|
|Kalendarza miesięcznego|MCN_SELCHANGE|
|Formant obrazu|(Nie dotyczy)|
|Postęp|NM_CUSTOMDRAW|
|Przycisk polecenia|BN_CLICKED|
|Przycisk radiowy|BN_CLICKED|
|Edycji wzbogaconej|EN_CHANGE|
|Pasek przewijania|NM_THEMECHANGED|
|Suwak|NM_CUSTOMDRAW|
|Pokrętła|UDN_DELTAPOS|
|Tekst statyczny|(Nie dotyczy)|
|Tab|TCN_SELCHANGE|
|Drzewo|TVN_SELCHANGE|

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Definiowanie zmiennych składowych dla kontrolek okna dialogowego](../windows/defining-member-variables-for-dialog-controls.md)<br/>
[Typy komunikatów związane z obiektami interfejsu użytkownika](../mfc/reference/message-types-associated-with-user-interface-objects.md)<br/>
[Edytowanie programu obsługi komunikatów](../mfc/reference/editing-a-message-handler.md)<br/>
[Definiowanie obsługi komunikatów dla komunikatów odbitych](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md)<br/>
[Deklarowanie zmiennej opartej na nowej klasie kontrolek](../mfc/reference/declaring-a-variable-based-on-your-new-control-class.md)<br/>
[Zastępowanie funkcji wirtualnych](../ide/overriding-a-virtual-function-visual-cpp.md)