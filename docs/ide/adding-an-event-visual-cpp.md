---
title: Dodaj zdarzenie
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.event.overview
helpviewer_keywords:
- ActiveX controls [C++], adding events to
- MFC ActiveX controls [C++], adding events
- events [C++], ActiveX controls
- add event wizard [C++]
ms.assetid: fe34832a-edfc-4f86-aacb-8df77001873d
ms.openlocfilehash: 1d5a8f5666dd04e00f8a438fdbf00320c37e14f4
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693428"
---
# <a name="add-an-event"></a>Dodaj zdarzenie

W widoku klas można dodać zdarzenia przy użyciu [Kreator dodawania zdarzenia](#add-event-wizard) tylko do klasy formantu w swojej [kontrolki MFC ActiveX](../mfc/reference/creating-an-mfc-activex-control.md) projektu. Jeśli chcesz dodać wydarzenie do innego typu projektu, użyj **zdarzenia** znajdujący się w [okno właściwości](/visualstudio/ide/reference/properties-window).

**Aby dodać wydarzenie do swojego projektu kontrolki MFC ActiveX:**

1. W widoku klas rozwiń węzeł projektu, aby wyświetlić klasy w projekcie.

1. Kliknij prawym przyciskiem myszy klasy formantu projektu.

1. W menu skrótów wybierz **Dodaj**, a następnie wybierz **Dodawanie zdarzenia** do wyświetlenia Kreator dodawania zdarzenia.

1. Podaj informacje o zdarzeniu w polach odpowiedniego kreatora.

1. Wybierz **Zakończ** do zdarzenia do projektu.

## <a name="in-this-section"></a>W tej sekcji

- [Kreator dodawania zdarzenia](#add-event-wizard)

## <a name="add-event-wizard"></a>Kreator dodawania zdarzenia

Ten kreator dodaje zdarzenie do projektu kontrolki MFC ActiveX. Można określić własne zdarzenia, dostosować typowe Zdarzenie standardowe lub wybierz z listy standardowych zdarzeń.

- **Nazwa zdarzenia**

   Ustawia nazwę używaną przez klientów automatyzacji do żądania zdarzenia z klasy. Wprowadź nazwę lub wybierz ją z listy.

- **Typ zdarzenia**

   Wskazuje typ zdarzenia do dodania. Dostępne tylko w przypadku wybrania z **Nazwa zdarzenia** listy.

   |Opcja|Opis|
   |------------|-----------------|
   |**Zapasów**|Określa, że zdarzenie, takie jak kliknięcie przycisku, zostaną zaimplementowane dla tej klasy. Zdarzenia podstawowe są definiowane w bibliotece Microsoft Foundation Class (MFC).|
   |**Custom**|Określa, że używasz własnej implementacji zdarzenia.|

- **Nazwa wewnętrzna**

   Ustawia nazwę funkcji składowej, która wysyła zdarzenie. Dostępne tylko dla niestandardowych zdarzeń. Nazwa opiera się na **Nazwa zdarzenia**. Można zmienić nazw wewnętrznych, jeśli chcesz podać nazwę różni się od **Nazwa zdarzenia**.

- **Typ parametru**

   Ustawia typ **Nazwa parametru**. Wybierz typ z listy.

- **Nazwa parametru**

   Określa nazwę parametru do przekazywania zdarzenia. Po wpisaniu nazwy, musisz wybrać **Dodaj** ją dodać listę parametrów.

   Po wybraniu **Dodaj**, nazwa parametru jest wyświetlana w **listy parametrów**.

   > [!NOTE]
   > Jeśli należy podać nazwę parametru, a następnie wybierz pozycję **Zakończ** przed wybraniem **Dodaj**, parametr nie jest dodawana do zdarzenia. Należy znaleźć metody i wstawić parametr ręcznie.

- **Add**

   Dodaje parametr należy określić w **Nazwa parametru**, a jego typ do **listy parametrów**. Wybierz **Dodaj** Aby dodać parametr do listy.

- **Usuń**

   Usuwa parametr w **listy parametrów** z listy.

- **Lista parametrów**

   Wyświetla wszystkie parametry i ich typy, które aktualnie dodane w metodzie. W miarę dodawania parametrów, kreator dokona aktualizacji **listy parametrów** do wyświetlenia każdego z parametrów za pomocą jego typu.
