---
title: Dodawanie klasy z formantu ActiveX (Visual C++) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 793adf38da33808371a0df71f671c3e29da75326
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "33322409"
---
# <a name="adding-a-class-from-an-activex-control-visual-c"></a>Dodawanie klasy z kontrolki ActiveX (Visual C++)
Ten kreator umożliwia tworzenie klasy MFC z interfejsu, dostępne kontrolki ActiveX. Można dodać klasy MFC do [aplikacji MFC](../mfc/reference/creating-an-mfc-application.md), [biblioteki MFC DLL](../mfc/reference/creating-an-mfc-dll-project.md), lub [kontrolki MFC ActiveX](../mfc/reference/creating-an-mfc-activex-control.md).  
  
> [!NOTE]
>  Nie ma konieczności tworzenia projektu MFC automatyzacji możliwość dodawania klasy z formantu ActiveX.  
  
 Formant ActiveX jest składnik oprogramowania wielokrotnego użytku, oparte na modelu obiektu składników (COM), obsługuje wiele funkcji OLE, który można dostosować do potrzeb wiele oprogramowania. Formanty ActiveX są przeznaczone do użycia zarówno w zwykłym kontenery formantów ActiveX w Internecie w strony sieci Web.  
  
### <a name="to-add-an-mfc-class-from-an-activex-control"></a>Dodawanie klasy MFC z formantu ActiveX  
  
1.  W jednym **Eksploratora rozwiązań** lub [widoku klasy](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925), kliknij prawym przyciskiem myszy nazwę projektu, do której chcesz dodać klasy formantu ActiveX.  
  
2.  W menu skrótów kliknij **Dodaj**, a następnie kliknij przycisk **Dodaj klasę**.  
  
3.  W [Dodaj klasę](../ide/add-class-dialog-box.md) kliknij okno dialogowe, w okienku szablonów **klasy MFC z formantu ActiveX**, a następnie kliknij przycisk **Otwórz** do wyświetlenia [dodawania klasy z ActiveX Kontrolowanie kreatora](../ide/add-class-from-activex-control-wizard.md).  
  
 W kreatorze można dodać więcej niż jeden interfejs formantu ActiveX. Podobnie można utworzyć klasy z więcej niż jeden formant ActiveX w jednej sesji kreatora.  
  
 Możesz dodawać klasy z kontrolki ActiveX w zarejestrowany w systemie, lub możesz dodawać klasy z kontrolki ActiveX znajduje się w plikach biblioteki typów (.tlb, .olb, dll, .ocx lub .exe) bez rejestrowania ich pierwszy w systemie. Zobacz [rejestrowanie OLE formanty](../mfc/reference/registering-ole-controls.md) Aby uzyskać więcej informacji o rejestrowaniu formantów ActiveX.  
  
 Kreator utworzy klasę MFC pochodną [CWnd](../mfc/reference/cwnd-class.md) lub [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md), dla każdego interfejsu należy dodać z wybranej kontrolki ActiveX.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Wprowadzenie do modelu COM i ATL](../atl/introduction-to-com-and-atl.md)