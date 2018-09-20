---
title: Dodawanie klasy z kontrolki ActiveX (Visual C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [C++], adding classes
- classes [C++], creating
ms.assetid: 729fcb37-54b8-44d5-9b4e-50bb16e0eea4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7fd284236d2e9267d281061eef3915ed41f6f590
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375959"
---
# <a name="adding-a-class-from-an-activex-control-visual-c"></a>Dodawanie klasy z kontrolki ActiveX (Visual C++)

Ten kreator umożliwia tworzenie klasy MFC z interfejsu, dostępne kontrolki ActiveX. Można dodać klasy MFC do [aplikacji MFC](../mfc/reference/creating-an-mfc-application.md), [biblioteki MFC DLL](../mfc/reference/creating-an-mfc-dll-project.md), lub [kontrolki MFC ActiveX](../mfc/reference/creating-an-mfc-activex-control.md).

> [!NOTE]
>  Nie trzeba tworzyć projektu MFC przy użyciu usługi Automation, możliwość dodawania klasy z kontrolki ActiveX.

Kontrolki ActiveX jest składnik oprogramowania wielokrotnego użytku, oparte na Component Object Model (COM) obsługuje szeroki zakres funkcji OLE, który można dostosować do potrzeb wiele oprogramowania. Kontrolki ActiveX są przeznaczone do użycia zarówno w zwykłych kontenery kontrolek ActiveX w Internecie w strony sieci Web.

### <a name="to-add-an-mfc-class-from-an-activex-control"></a>Dodawanie klasy MFC z formantu ActiveX

1. W obu **Eksploratora rozwiązań** lub [Widok klas](/visualstudio/ide/viewing-the-structure-of-code), kliknij prawym przyciskiem myszy nazwę projektu, do którego chcesz dodać klasy kontrolki ActiveX.

1. W menu skrótów kliknij **Dodaj**, a następnie kliknij przycisk **Dodaj klasę**.

1. W [Dodaj klasę](../ide/add-class-dialog-box.md) kliknij w okienku szablonów, w oknie dialogowym **klasy MFC z formantu ActiveX**, a następnie kliknij przycisk **Otwórz** do wyświetlenia [dodawania klasy z ActiveX Kontrolowanie kreatora](../ide/add-class-from-activex-control-wizard.md).

W kreatorze możesz dodać więcej niż jeden interfejs w kontrolce ActiveX. Podobnie można utworzyć klasy z więcej niż jeden formant ActiveX w jednej sesji kreatora.

Można dodać klasy z kontrolki ActiveX zarejestrowany w systemie, lub można dodać klasy z kontrolki ActiveX na terenie typów plików biblioteki (.tlb, .olb, .dll, .ocx lub .exe) bez rejestrowania ich pierwszy w systemie. Zobacz [rejestrowanie OLE formantów](../mfc/reference/registering-ole-controls.md) więcej informacji na temat rejestrowania formantów ActiveX.

Kreator utworzy klasę MFC pochodną [CWnd](../mfc/reference/cwnd-class.md) lub [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md), dla każdego interfejsu, możesz dodać z wybranej kontrolki ActiveX.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)<br>
[Wprowadzenie do modelu COM i ATL](../atl/introduction-to-com-and-atl.md)