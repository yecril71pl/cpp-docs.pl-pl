---
title: Kreator dodawania metody | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.method.overview
dev_langs:
- C++
helpviewer_keywords:
- Add Method Wizard [C++]
- methods [C++], adding using wizards
ms.assetid: b9a71b0e-9ecf-40fa-9f86-4200cb23d671
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 45c3b0ca9a3e6c88e4ae40a5eb52aeb3223d2860
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46397305"
---
# <a name="add-method-wizard"></a>Kreator dodawania metody

Użyj tego kreatora, aby dodać metodę do interfejsu. W zależności od typu projektu lub typu interfejsu, do którego dodajesz metodę Kreator wyświetli inne opcje.

## <a name="names"></a>Nazwy

- **Zwracany typ**

   Typ danych zwracany przez metodę. `HRESULT` Zaleca się dla wszystkich typów interfejsu, ponieważ zawiera ono standardowy sposób zwracane błędy.

   |Typ interfejsu|Opis|
   |--------------------|-----------------|
   |Podwójnego interfejsu|`HRESULT`. Nie będzie zmieniana.|
   |Niestandardowy interfejs|`HRESULT`. Nie będzie zmieniana.|
   |Lokalny interfejs niestandardowe|Podaj swój własny typ zwracany lub wybierz z listy.|
   |Dispinterface|Podaj swój własny typ zwracany lub wybierz z listy.|
   |Dispinterface kontrolki MFC ActiveX|W przypadku zastosowania metody akcji, zwracany typ ma ustawioną wartość odpowiednią i można zmienić. Jeśli zostanie wybrana metoda z **nazwę metody** listy, a następnie kliknij przycisk **niestandardowe** w obszarze **wybierz typ metody**, wybierz typ zwracany z listy.|

- **Nazwa metody**

   Ustawia nazwę metody.

   |Typ interfejsu|Opis|
   |--------------------|-----------------|
   |ATL podwójnego interfejsu, niestandardowego interfejsu i lokalne niestandardowy interfejs|Podaj nazwę metody.|
   |MFC dispinterface|Podaj własną nazwę metody lub wybierz nazwę sugerowane metody z listy. Jeśli wybierzesz nazwę z listy odpowiednią wartość pojawia się w **zwracany typ** pole to nie będzie zmieniana.|
   |Dispinterface kontrolki MFC ActiveX|Podaj własny lub wybrać jedną z metod standardowych [DoClick](../mfc/reference/colecontrol-class.md#doclick) i [Odśwież](../mfc/reference/colecontrol-class.md#refresh). Zobacz [kontrolki ActiveX MFC: dodawanie metod akcji](../mfc/mfc-activex-controls-adding-stock-methods.md) Aby uzyskać więcej informacji.|

- **Typ metody**

   Dostępne tylko dla kontrolek MFC ActiveX. Jeśli podasz nazwę metody w **nazwę metody** polu, zamiast wybierania metody na liście, to pole jest niedostępne.

   Po wybraniu jednej z metod w **nazwę metody** wybierz implementacji standardowych lub niestandardowych implementacji.

   |Typ metody|Opis|
   |-----------------|-----------------|
   |**Zapasów**|Domyślnie. Wstawia podstawowe implementacji metody, wybierz w **nazwę metody** listy. **Zwracany typ** można zmienić, jeśli zostanie wybrana **Stock**.|
   |**Niestandardowy**|Wstawia z implementacją wycinka Metoda wybrana w **nazwę metody** listy. W przypadku typów niestandardową metodę możesz podać swój własny typ zwracany lub możesz wybrać jeden z **zwracany typ** listy.|

- **Nazwa wewnętrzna**

   Dostępne tylko niestandardowych metod, dodane do dispinterface MFC. Ustawia nazwę używaną w Mapa wysyłania pliku nagłówka (.h) i plik implementacji (.cpp). Domyślnie ta nazwa jest taka sama jak **nazwę metody**. Możesz zmienić nazwę metody, jeśli pracujesz z dispinterface MFC lub Jeśli dodajesz niestandardową metodę do dispinterface kontrolki MFC ActiveX.

   |Typ interfejsu|Opis|
   |--------------------|-----------------|
   |ATL podwójnego interfejsu, niestandardowego interfejsu i lokalne niestandardowy interfejs|Niedostępne|
   |MFC dispinterface|Domyślnie w nazwie metody. Można edytować nazwy wewnętrznej.|
   |Dispinterface kontrolki MFC ActiveX|Możesz ustawić nazwa wewnętrzna tylko w przypadku niestandardowych metod. Metody akcji nie należy używać nazw wewnętrznych.|

- **Atrybuty parametru**

   Ustawia wszelkie dodatkowe atrybuty dla określonego w parametrze **Nazwa parametru**.

   |Atrybut parametru|Opis|Dozwolone kombinacje|
   |-------------------------|-----------------|--------------------------|
   |**W**|Wskazuje, że parametr jest przekazywany z procedury wywołującej do procedury wywoływanej.|**w** tylko<br /><br /> **w** i **out**|
   |**limit**|Wskazuje, że parametr wskaźnika jest zwracana z procedury wywoływanej do procedury wywołującej (z serwera do klienta).|**limit** tylko<br /><br /> **w** i **out**<br /><br /> **limit** i **retval**|
   |**retval**|Wskazuje, że parametr otrzymuje wartość zwrotną z elementu członkowskiego.|**retval** i komentarz|

- **Typ parametru**

   Ustawia typ danych parametru. Wybierz typ z listy.

- **Nazwa parametru**

   Określa nazwę parametru, aby przechodzić przez metodę. Po wpisaniu nazwy, należy kliknąć przycisk **Dodaj** ją dodać do listy parametrów, które będzie przekazywał metodę. Jeśli nazwa parametru nie jest określona, Kreator ignoruje wszelkie atrybuty parametru (tylko ATL) lub **typ parametru** wybrane opcje.

   Po kliknięciu **Dodaj**, nazwa parametru jest wyświetlana w **listy parametrów**.

   > [!Note]
   > Jeśli należy podać nazwę parametru, a następnie kliknij przycisk **Zakończ** przed kliknięciem przycisku **Dodaj**, parametr nie zostanie dodany do metody. Należy znaleźć metody i wstawić parametr ręcznie.

- **Add**

   Dodaje parametr należy określić w **Nazwa parametru**i jego atrybuty typu i parametr do **listy parametrów**. Należy kliknąć przycisk **Dodaj** Aby dodać parametr do listy.

- **Usuń**

   Usuwa parametr w **listy parametrów** z listy.

- **Lista parametrów**

   Wyświetla wszystkie parametry i ich Modyfikatory i typów dodanych w aktualnie dla metody. W miarę dodawania parametrów, kreator dokona aktualizacji **listy parametrów** do wyświetlenia każdego parametru, z modyfikatora i typu.

## <a name="see-also"></a>Zobacz też

[Dodawanie metody](../ide/adding-a-method-visual-cpp.md)<br/>
[Atrybuty IDL, Kreator dodawania metody](../ide/idl-attributes-add-method-wizard.md)