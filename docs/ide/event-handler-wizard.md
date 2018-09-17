---
title: Kreator obsługi zdarzeń | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.eventhandler.overview
dev_langs:
- C++
helpviewer_keywords:
- Event Handler Wizard [C++]
ms.assetid: af8e1835-94b1-4d9a-b353-c519e011d3a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4c2ff441fc38d460e27039d7825753a2011dac3e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702770"
---
# <a name="event-handler-wizard"></a>Kreator obsługi zdarzeń
Ten kreator dodaje program obsługi zdarzeń dla formantu pola okna dialogowego do klasy wybranych przez użytkownika. Po dodaniu programu obsługi zdarzeń z [okno właściwości](/visualstudio/ide/reference/properties-window), można go dodać tylko do klasy, która implementuje okno dialogowe. Zobacz [Dodawanie obsługi zdarzeń dla formantów okna dialogowego](../windows/adding-event-handlers-for-dialog-box-controls.md) Aby uzyskać więcej informacji.  
  
- **Nazwa polecenia**

   Identyfikuje zaznaczonego formantu, do którego jest dodawany program obsługi zdarzeń. To pole jest niedostępne.  
  
- **Typ komunikatu**

   Wyświetla listę bieżącej obsługi komunikatów możliwe dla zaznaczonej kontrolki.  
  
- **Nazwa procedury obsługi — funkcja**

   Wyświetla nazwę funkcji, który jest dodawany do obsługi zdarzeń. Domyślnie nazwa opiera się na typ komunikatu i polecenia dołączony przez "Włączone". Na przykład dla przycisku o nazwie `IDC_BUTTON1`, typ komunikatu `BN_CLICKED` Wyświetla nazwę procedury obsługi funkcji `OnBnClickedButton1`.  
  
- **Lista klas**

   Wyświetla dostępne klasy, do których można dodać program obsługi zdarzeń. Klasa wybranego okna dialogowego jest wyświetlany w kolorze czerwonym.  
  
- **Opis procedury obsługi**

   Zawiera opis elementu zaznaczonego w **typ komunikatu** pole. To pole jest niedostępne.  
  
- **Dodawanie i edytowanie**

   Dodaje program obsługi komunikatów do wybranej klasy lub obiekt, a następnie otwiera edytor tekstu na nową funkcję, więc można dodać kod procedury obsługi powiadamiania kontrolki.  
  
- **Edytowanie kodu**

   Zostanie otwarty Edytor tekstów, aby wybrane istniejącą funkcję, dzięki czemu można dodawać lub edytować kod procedury obsługi powiadamiania kontrolki.  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie obsługi zdarzeń](../ide/adding-an-event-handler-visual-cpp.md)