---
title: "Kreator obsługi zdarzeń | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.eventhandler.overview
dev_langs: C++
helpviewer_keywords: Event Handler Wizard [C++]
ms.assetid: af8e1835-94b1-4d9a-b353-c519e011d3a1
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0f2f871381f64627caa76c28c5195143e1b391f0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="event-handler-wizard"></a>Kreator obsługi zdarzeń
Ten kreator dodaje program obsługi zdarzeń dla kontrolka okna dialogowego do wybranej klasy. Po dodaniu obsługi zdarzeń z [okna właściwości](/visualstudio/ide/reference/properties-window), można dodać go tylko do klasy, która implementuje okno dialogowe. Zobacz [Dodawanie obsługi zdarzeń dla formantów okna dialogowego](../windows/adding-event-handlers-for-dialog-box-controls.md) Aby uzyskać więcej informacji.  
  
 **Nazwa polecenia**  
 Określa wybrany formant, do którego jest dodawany program obsługi zdarzeń. To pole jest niedostępne.  
  
 **Typ komunikatu**  
 Wyświetla listę bieżącej obsługi komunikatów możliwe zaznaczonego formantu.  
  
 **Nazwa programu obsługi — funkcja**  
 Wyświetla nazwę funkcji, która jest dodawana do obsługi zdarzenia. Domyślnie nazwa opiera się na typ komunikatu i polecenia reprezentowana przez "On". Na przykład przycisk o nazwie `IDC_BUTTON1`, typ komunikatu `BN_CLICKED` Wyświetla nazwę obsługi funkcji `OnBnClickedButton1`.  
  
 **Lista klas**  
 Wyświetla dostępne klasy, do których można dodać obsługi zdarzeń. Klasy dla okna dialogowego wybranego jest wyświetlany na czerwono.  
  
 **Opis programu obsługi**  
 Zawiera opis elementu zaznaczonego w **typ komunikatu** pole. To pole jest niedostępne.  
  
 **Dodawanie i edytowanie**  
 Dodaje program obsługi komunikatów do wybranej klasy lub obiekt, a następnie otworzeniem nowa funkcja w edytorze tekstu, można dodać kod obsługi powiadamiania kontrolki.  
  
 **Edytowanie kodu**  
 Zostanie otwarty w edytorze tekstu wybranej istniejącej funkcji, można dodawać lub edytować kod obsługi powiadamiania kontrolki.  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie obsługi zdarzeń](../ide/adding-an-event-handler-visual-cpp.md)