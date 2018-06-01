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
ms.openlocfilehash: cc2ebd18640f0ab778cb45252691e63206861d53
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "33340349"
---
# <a name="add-method-wizard"></a>Kreator dodawania metody
Ten kreator umożliwia dodawanie metody do interfejsu. W zależności od typu projektu lub typ interfejsu, do którego dodajesz metody Kreator wyświetli różne opcje.  
  
## <a name="names"></a>Nazwy  
 **Zwracany typ**  
 Typ danych zwracanych przez metodę. `HRESULT` Zaleca się dla wszystkich typów interfejsu, ponieważ zapewnia standardowy sposób zwracać błędów.  
  
|Typ interfejsu|Opis|  
|--------------------|-----------------|  
|Podwójna — interfejs|`HRESULT`. Niezmienne.|  
|Niestandardowy interfejs|`HRESULT`. Niezmienne.|  
|Niestandardowy interfejs lokalnego|Podaj własny typ zwracany albo wybierz z listy.|  
|Dispinterface|Podaj własny typ zwracany albo wybierz z listy.|  
|Dispinterface kontrolki MFC ActiveX|W przypadku zastosowania metody akcji, zwracany typ jest ustawiona na odpowiednią wartość i jest niezmienne. W przypadku wybrania metody z **nazwę metody** listy i kliknij przycisk **niestandardowy** w obszarze **wybierz typ metody**, wybierz typ zwracany z listy.|  
  
 **Nazwa metody**  
 Ustawia nazwę metody.  
  
|Typ interfejsu|Opis|  
|--------------------|-----------------|  
|Interfejs podwójny ATL, niestandardowy interfejs i lokalne niestandardowy interfejs|Podaj nazwę metody.|  
|MFC dispinterface|Podaj nazwę metody lub wybierz nazwę sugerowane metody z listy. W przypadku wybrania nazwę z listy odpowiednią wartość znajduje się w **zwracany typ** pole ma zmieniać.|  
|Dispinterface kontrolki MFC ActiveX|Podaj własny lub wybrać jedną z metod standardowych [DoClick](../mfc/reference/colecontrol-class.md#doclick) i [Odśwież](../mfc/reference/colecontrol-class.md#refresh). Zobacz [kontrolki ActiveX MFC: dodawanie metod giełdowych](../mfc/mfc-activex-controls-adding-stock-methods.md) Aby uzyskać więcej informacji.|  
  
 **Typ — metoda**  
 Dostępne tylko w przypadku kontrolek MFC ActiveX. Jeśli podasz nazwę metody w **nazwę metody** polu, zamiast wybierać metodę z listy, to pole jest niedostępne.  
  
 Po wybraniu jednej z metod w **nazwę metody** wybierz implementacji standardowych lub niestandardowych implementacji.  
  
|Typ — metoda|Opis|  
|-----------------|-----------------|  
|**Zapasów**|Domyślnie. Wstawia standardowych implementacja metody, należy wybrać w **nazwę metody** listy. **Zwracany typ** jest zmieniać w przypadku wybrania **giełdowych**.|  
|**Niestandardowy**|Wstawia implementacji programu klasy zastępczej metody wybrany w **nazwę metody** listy. Dla typów niestandardowej metody, można podać własne zwracany typ lub możesz wybrać jeden z **zwracany typ** listy.|  
  
 **Nazwa wewnętrzna**  
 Dostępne tylko niestandardowych metod dodane do dispinterface MFC. Ustawia nazwę używaną w mapy wysyłania plików nagłówków (.h) i pliku implementacji (.cpp). Domyślnie ta nazwa jest taka sama jak **nazwę metody**. Jeśli pracujesz z dispinterface MFC lub dodajesz niestandardowe metody do dispinterface kontrolki MFC ActiveX, można zmienić nazwę metody.  
  
|Typ interfejsu|Opis|  
|--------------------|-----------------|  
|Interfejs podwójny ATL, niestandardowy interfejs i lokalne niestandardowy interfejs|Niedostępne|  
|MFC dispinterface|Domyślnie w nazwie metody. Można edytować nazwy wewnętrznej.|  
|Dispinterface kontrolki MFC ActiveX|Można ustawić tylko dla metod niestandardowych wewnętrzna nazwa. Podstawowe metody nie należy używać wewnętrzna nazwa.|  
  
 **Atrybuty parametrów**  
 Ustawia wszelkie dodatkowe atrybuty parametru określone w **Nazwa parametru**.  
  
|Atrybut parametru|Opis|Dozwolone kombinacje|  
|-------------------------|-----------------|--------------------------|  
|**W**|Wskazuje, że parametr jest przekazywany z procedury wywołującej do procedury wywoływanej.|**w** tylko<br /><br /> **w** i **out**|  
|**limit**|Wskazuje, że parametr wskaźnika jest zwracana z procedury wywoływanej do procedury wywołującej (z serwera do klienta).|**limit** tylko<br /><br /> **w** i **out**<br /><br /> **limit** i **retval**|  
|**retval**|Wskazuje, że parametr otrzymuje wartość zwrotną z elementu członkowskiego.|**retval** i out|  
  
 **Typ parametru**  
 Ustawia typ danych parametru. Wybierz typ z listy.  
  
 **Nazwa parametru**  
 Ustawia nazwę parametru przekazywane do metody. Po wpisaniu nazwy, należy kliknąć opcję **Dodaj** dodać ją do listy parametrów, które mają być przekazywane metodę. Jeśli nazwa parametru nie jest określona, Kreator ignoruje wszystkie atrybuty parametru (tylko ATL) lub **typ parametru** wybrane opcje.  
  
 Po kliknięciu **Dodaj**, nazwa parametru jest wyświetlana w **listy parametrów**.  
  
 **Uwaga** Jeśli podać nazwę parametru, a następnie kliknij przycisk **Zakończ** przed kliknięciem przycisku **Dodaj**, parametr nie zostanie dodany do metody. Należy znaleźć metody i Wstaw parametr ręcznie.  
  
 **Dodaj**  
 Dodaje parametr należy określić w **Nazwa parametru**i jego atrybuty typu i parametru do **listy parametrów**. Należy kliknąć opcję **Dodaj** powoduje dodanie parametru do listy.  
  
 **Usuń**  
 Usuwa parametr należy wybrać w **listy parametrów** z listy.  
  
 **Listy parametrów**  
 Wyświetla wszystkie parametry i Modyfikatory i typy aktualnie dodanych w metodzie. Jak dodać parametry, Kreator aktualizuje **listy parametrów** do wyświetlania każdego parametru z modyfikatora i typu.  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie metody](../ide/adding-a-method-visual-cpp.md)   
 [Atrybuty IDL, Kreator dodawania metody](../ide/idl-attributes-add-method-wizard.md)