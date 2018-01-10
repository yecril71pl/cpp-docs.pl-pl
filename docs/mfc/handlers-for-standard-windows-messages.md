---
title: "Programy obsługi dla standardowych komunikatów systemu Windows | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: afx_msg
dev_langs: C++
helpviewer_keywords:
- Windows messages [MFC], handlers
- message handling [MFC], Windows message handlers
- handler functions, standard Windows messages
- functions [MFC], handler
- messages [MFC], Windows
ms.assetid: 19412a8b-2c38-4502-81da-13c823c7e36c
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 91df3462297c2a45a8938d815cc3b6a3b8ca6edb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="handlers-for-standard-windows-messages"></a>Programy obsługi dla standardowych komunikatów systemu Windows
Domyślne programy obsługi dla standardowych komunikatów systemu Windows (**WM_**) są wstępnie zdefiniowane w klasie `CWnd`. Biblioteka klas podstawowych nazwy dla tych programów obsługi na nazwę komunikatu. Na przykład program obsługi dla `WM_PAINT` komunikat jest zadeklarowana w `CWnd` jako:  
  
 `afx_msg void OnPaint();`  
  
 **Afx_msg** — słowo kluczowe sugeruje efekt C++ **wirtualnego** — słowo kluczowe podział obsługi z innych `CWnd` funkcji elementów członkowskich. Jednak te funkcje nie są faktycznie wirtualnych; Zamiast tego są implementowane za pośrednictwem mapy komunikatów. Mapy komunikatów zależą od wyłącznie standardowe makra preprocesora, nie na jakichkolwiek rozszerzeń języka C++. **Afx_msg** — słowo kluczowe jest rozpoznawana jako biały znak po przetwarzania wstępnego.  
  
 Aby zastąpić obsługi zdefiniowana w klasie podstawowej, po prostu zdefiniuj funkcję z tej samej prototypu w klasie pochodnej i wpisu mapy komunikatów dla programu obsługi. Programu obsługi "przesłania" wszelkie obsługi o takiej samej nazwie w jednym z klas podstawowych swojej klasy.  
  
 W niektórych przypadkach programu obsługi powinny wywoływać przesłoniętych obsługi w klasie podstawowej, klasy podstawowej i systemu Windows może działać w komunikacie. Gdzie wywołania obsługi klasy podstawowej w zastąpienia zależy od okoliczności. Czasami należy najpierw wywołać obsługi klasy podstawowej i czasami ostatni. Czasami użytkownik wywołania klasy podstawowej obsługi warunkowo, jeśli nie chcesz samodzielnie obsługi wiadomości. Czasami powinny wywoływać program klasy podstawowej, należy wydać warunkowo swoim własnym kodem obsługi, w zależności od wartości lub stanu zwrócony przez program obsługi klasy podstawowej.  
  
> [!CAUTION]
>  Nie jest bezpieczne Argumenty przekazane do programu obsługi, jeśli zamierzasz przekazać je do obsługi klasy podstawowej. Na przykład może się wydawać się zmodyfikować `nChar` argument `OnChar` obsługi (do przekonwertowania na wielkie litery, na przykład). To zachowanie jest dość zasłoniętej, ale jeśli niezbędne podczas wykonywania tego efektu `CWnd` funkcji członkowskiej **SendMessage** zamiast tego.  
  
 Jak można ustalić prawidłowego sposobem zastąpić danej wiadomości, gdy okno właściwości zapisuje szkielet funkcji obsługi dla danego komunikatu — `OnCreate` obsługę `WM_CREATE`, na przykład — szkice go w formie zalecanej przesłonięcia funkcji członkowskiej. Poniższy przykład zaleca obsługi najpierw wywołania obsługi klasy podstawowej i kontynuować tylko pod warunkiem, że nie zwraca -1.  
  
 [!code-cpp[NVC_MFCMessageHandling#3](../mfc/codesnippet/cpp/handlers-for-standard-windows-messages_1.cpp)]  
  
 Konwencja nazwy te programy obsługi rozpoczynać się od prefiksu "On". Niektóre z tych programów obsługi nie przyjmują argumentów, podczas gdy inne wykorzystują w kilku. Niektóre również mieć zwracanego typu innego niż `void`. Programy obsługi domyślnego dla wszystkich **WM_** komunikaty są udokumentowane w *dokumentacja MFC* jako funkcje elementu członkowskiego klasy `CWnd` których nazwy zaczynają się od "Na". Deklaracje funkcji Członkowskich w `CWnd` mają przedrostek **afx_msg**.  
  
## <a name="see-also"></a>Zobacz też  
 [Deklarowanie funkcji obsługi komunikatów](../mfc/declaring-message-handler-functions.md)
