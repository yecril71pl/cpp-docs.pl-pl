---
title: Kreator dodawania zdarzenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.event.overview
dev_langs:
- C++
helpviewer_keywords:
- Add Event Wizard [C++]
ms.assetid: bdd2a7bb-13d5-44d7-abc9-e785ba4e05ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f3c12be98fa94e5109d5113ef65901972bff59a5
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703615"
---
# <a name="add-event-wizard"></a>Kreator dodawania zdarzenia
Ten kreator dodaje zdarzenie do projektu kontrolki MFC ActiveX. Można określić własne zdarzenia, można dostosować zdarzenie zazwyczaj standardowe lub możesz wybrać z listy zdarzeń standardowych.  
  
- **Nazwa zdarzenia**  

   Ustawia nazwę używaną przez klientów automatyzacji do żądania zdarzenia z klasy. Wprowadź nazwę lub wybierz ją z listy.  
  
- **Typ zdarzenia**  

   Wskazuje typ zdarzenia do dodania. Dostępne tylko w przypadku wybrania z **Nazwa zdarzenia** listy.  
  
   |Opcja|Opis|
   |------------|-----------------|
   |**Zapasów**|Określa, że zdarzenie, takie jak kliknięcie przycisku, zostaną zaimplementowane dla tej klasy. Zdarzenia podstawowe są definiowane w bibliotece Microsoft Foundation Class (MFC).|
   |**Niestandardowy**|Określa, udostępniają implementacji zdarzenia.|

- **Nazwa wewnętrzna**  

   Ustawia nazwę funkcji składowej, która wysyła zdarzenie. Dostępne tylko dla niestandardowych zdarzeń. Nazwa opiera się na **Nazwa zdarzenia**. Można zmienić nazw wewnętrznych, jeśli chcesz podać nazwę różni się od **Nazwa zdarzenia**.  
  
- **Typ parametru**  

   Ustawia typ **Nazwa parametru**. Wybierz typ z listy.  
  
- **Nazwa parametru**  

   Określa nazwę parametru do przekazywania zdarzenia. Po wpisaniu nazwy, należy kliknąć przycisk **Dodaj** ją dodać listę parametrów.  
  
   Po kliknięciu **Dodaj**, nazwa parametru jest wyświetlana w **listy parametrów**.  
  
   > [!NOTE]
   > Jeśli należy podać nazwę parametru, a następnie kliknij przycisk **Zakończ** przed kliknięciem przycisku **Dodaj**, parametr nie jest dodawana do zdarzenia. Należy znaleźć metody i wstawić parametr ręcznie. **Lista parametrów**  
  
- **Add**  

   Dodaje parametr należy określić w **Nazwa parametru**, a jego typ do **listy parametrów**. Należy kliknąć przycisk **Dodaj** Aby dodać parametr do listy.  
  
- **Usuń**  

   Usuwa parametr w **listy parametrów** z listy.  
  
- **Lista parametrów**  

   Wyświetla wszystkie parametry i ich typy, które aktualnie dodane w metodzie. W miarę dodawania parametrów, kreator dokona aktualizacji **listy parametrów** do wyświetlenia każdego z parametrów za pomocą jego typu.  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie zdarzenia](../ide/adding-an-event-visual-cpp.md)