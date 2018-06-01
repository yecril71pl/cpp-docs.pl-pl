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
ms.openlocfilehash: f92f871f22fb01f3f0f37677c393fcd481c08120
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "33325198"
---
# <a name="add-event-wizard"></a>Kreator dodawania zdarzenia
Ten kreator dodaje zdarzenia do projektu kontrolki MFC ActiveX. Możesz określić własne zdarzenia, można dostosować zwykle standardowych zdarzeń, lub możesz wybrać z listy zdarzeń standardowych.  
  
 **Nazwa zdarzenia**  
 Ustawia nazwę używaną przez klientów automatyzacji do żądania zdarzenia z klasy. Wprowadź nazwę lub wybierz ją z listy.  
  
 **Typ zdarzenia**  
 Wskazuje typ zdarzenia do dodania. Dostępne tylko w przypadku wybrania z **Nazwa zdarzenia** listy.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**Zapasów**|Określa, że zdarzenie standardowe, takie jak kliknij przycisk, będzie zaimplementowana dla tej klasy. Standardowych zdarzeń są definiowane w bibliotece Microsoft Foundation Class (MFC).|  
|**Niestandardowy**|Określa, że udostępniasz implementacji zdarzenia.|  
  
 **Nazwa wewnętrzna**  
 Ustawia nazwę funkcji członkowskiej, która wysyła zdarzenie. Dostępne tylko dla niestandardowych zdarzeń. Nazwa jest oparta na **Nazwa zdarzenia**. Można zmienić nazwy wewnętrznej, jeśli chcesz podać nazwę inną niż **Nazwa zdarzenia**.  
  
 **Typ parametru**  
 Ustawia typ **Nazwa parametru**. Wybierz typ z listy.  
  
 **Nazwa parametru**  
 Ustawia nazwę parametru do przekazywania wydarzenia. Po wpisaniu nazwy, należy kliknąć opcję **Dodaj** ją dodać listę parametrów.  
  
 Po kliknięciu **Dodaj**, nazwa parametru jest wyświetlana w **listy parametrów**.  
  
> [!NOTE]
>  Jeśli musisz podać nazwę parametru, a następnie kliknij przycisk **Zakończ** przed kliknięciem przycisku **Dodaj**, parametr nie jest dodawana do zdarzenia. Należy znaleźć metody i Wstaw parametr ręcznie. **Listy parametrów**  
  
 **Dodaj**  
 Dodaje parametr należy określić w **Nazwa parametru**, a jego typ do **listy parametrów**. Należy kliknąć opcję **Dodaj** powoduje dodanie parametru do listy.  
  
 **Usuń**  
 Usuwa parametr należy wybrać w **listy parametrów** z listy.  
  
 **Listy parametrów**  
 Wyświetla wszystkie parametry i typy aktualnie dodanych w metodzie. Jak dodać parametry, Kreator aktualizuje **listy parametrów** do wyświetlania każdego parametru z typem.  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie zdarzenia](../ide/adding-an-event-visual-cpp.md)