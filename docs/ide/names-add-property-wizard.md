---
title: Nazwy, Kreator dodawania właściwości | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.prop.overview
dev_langs:
- C++
ms.assetid: 0453b7ea-89cb-41a1-80a2-d45f61589c0a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ac71d4713a71833886e577106f4bd8fd6565014a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410614"
---
# <a name="names-add-property-wizard"></a>Nazwy, Dodaj kreatora właściwości

Użyj tego kreatora, aby dodać właściwość do interfejsu.

- **Typ właściwości**

   Ustawia typ właściwości, które dodajesz. Dla dispinterfaces MFC Podaj swój własny typ, lub wybierz z listy wstępnie zdefiniowanych. Jeśli podasz podstawowego wdrożenia właściwość **typ właściwości** ustawiono typu podstawowego, a jest niedostępna w przypadku zmiany.

- **Nazwa właściwości**

   Ustawia nazwę właściwości. Dispinterfaces MFC związane z kontrolkami ActiveX możesz podać własną nazwę lub nazwy podstawowe właściwości można wybrać z listy wstępnie zdefiniowanych. Jeśli podasz swoją własną nazwę właściwości **Stock** typ wdrożenia nie jest dostępny. Zobacz [właściwości podstawowe](../ide/stock-properties.md) opis właściwości na liście.

   |Typ interfejsu|Opis|
   |--------------------|-----------------|
   |ATL podwójnego interfejsu, niestandardowego interfejsu i lokalne niestandardowy interfejs|Podaj nazwę właściwości.|
   |Dispinterface MFC, dispinterface kontrolki MFC ActiveX|Podaj nazwę właściwości lub wybierz właściwości podstawowych, z listy. Jeśli wybierzesz właściwość z listy odpowiednią wartość pojawia się w **typ właściwości** pola. Można zmienić tego typu, w zależności od wyboru w obszarze **typ implementacji**.|

- **Zwracany typ**

   Tylko ATL interfejsów. Ustawia typ zwrotny dla właściwości. Podwójne interfejsy `HRESULT` jest zawsze typem zwracanym, a to pole jest niedostępne. Dla interfejsów niestandardowych można wybrać typ zwracany z listy. `HRESULT` nadal zaleca się, ponieważ zawiera ono standardowy sposób zwracane błędy.

- **Nazwa zmiennej**

   Tylko dispinterfaces MFC. Dostępne tylko w przypadku określenia **zmiennej składowej** w obszarze **typ implementacji**. Określa nazwę zmiennej składowej, z którą właściwość jest skojarzony. Domyślnie, nazwa zmiennej jest równa m_*PropertyName*. Możesz edytować tę nazwę.

- **Funkcja powiadomień**

   Tylko dispinterfaces MFC. Dostępne tylko w przypadku określenia **zmiennej składowej** w obszarze **typ implementacji**. Ustawia nazwę powiadomień funkcji o nazwie, jeśli zmiany właściwości. Domyślnie, nazwa funkcji powiadomień jest włączona*PropertyName*zmieniono. Możesz edytować tę nazwę.

- **Funkcja Get**

   Aby uzyskać MFC dispinterfaces. Dostępne tylko w przypadku określenia **metod Get/Set** w obszarze **typ implementacji**. Ustawia nazwę funkcji do pobrania właściwości. Domyślnie, nazwa funkcji Get jest równa Get*PropertyName*. Możesz edytować tę nazwę. Jeśli usuniesz nazwę funkcji [getnotsupported —](../mfc/reference/colecontrol-class.md#getnotsupported) są wstawiane do mapy wysyłania interfejsu. Get*PropertyName* funkcji określa, że właściwość do odczytu.

- **Funkcja set**

   Tylko dispinterfaces MFC. Dostępne tylko w przypadku określenia **metod Get/Set** w obszarze **typ implementacji**. Ustawia nazwę funkcji, należy ustawić właściwości. Domyślnie, nazwa funkcji Set jest równa zestaw*PropertyName*. Możesz edytować tę nazwę. Jeśli usuniesz nazwę funkcji [setnotsupported —](../mfc/reference/colecontrol-class.md#setnotsupported) są wstawiane do mapy wysyłania interfejsu. Zestaw*PropertyName* funkcji określa, czy właściwość jest zapisywalna.

- **Typ implementacji**

   Tylko dispinterfaces MFC. Określa, jak implementować właściwość, do którego dodajesz.

   |Typ implementacji|Opis|
   |-------------------------|-----------------|
   |**Zapasów**|Określa podstawowe implementacji właściwości wybranego w **nazwa właściwości**. Domyślnie. Zobacz [właściwości podstawowe](../ide/stock-properties.md) Aby uzyskać więcej informacji.<br /><br /> Jeśli określisz **Stock**, następnie **typ właściwości**, **typ parametru**, i **Nazwa parametru** są wygaszone.|
   |**Zmienna składowa**|Określa, że właściwość została dodana jako zmienną składową. Można dodać właściwości niestandardowe lub większość właściwości podstawowe, jako zmienne Członkowskie. Nie można określić **zmiennej składowej** dla **podpis**, **hWnd**, i **tekstu** właściwości.<br /><br /> Udostępnia domyślne nazwy w obszarze **nazwa zmiennej** i **funkcję powiadomień**. Możesz edytować tę nazwę.|
   |**Metody GET/Set**|Określa właściwość jest dodawany jako Get*PropertyName* i ustaw*PropertyName* funkcje domyślne. Te nazwy są wyświetlane w obszarze **Get — funkcja** i **funkcja Set**.<br /><br /> Domyślne można zmienić **typ właściwości**, która przekazuje wartość dla funkcji Get. Można określić parametry **uzyskać** i `Set` funkcji.|

- **Funkcja Get**

   ATL interfejsów. Ustawia właściwość jako do odczytu; oznacza to, tworzy **uzyskać** metodę pobierania tej właściwości z obiektu. Musisz wybrać **uzyskać**, `Put`, lub obu.

- **Umieść — funkcja**

   Tylko ATL interfejsów. Ustawia właściwość zapisywalnej; oznacza to, tworzy `Put` metoda ustawienie lub "wprowadzenie", ta właściwość obiektu. Musisz wybrać **uzyskać**, `Put`, lub obu. Jeśli wybierzesz tę opcję, można wybrać z dwóch poniższych sposobów, aby wdrożyć metodę:

   |Opcja|Opis|
   |------------|-----------------|
   |**PropPut**|[PropPut](../windows/propput.md) funkcja zwraca kopię obiektu. Jest to domyślny i najbardziej popularny sposób, aby ustawić właściwość jako zapisu.|
   |**PropPutRef**|[PropPutRef](../windows/propputref.md) funkcja zwraca odwołanie do obiektu, a nie zwraca kopię obiektu. Rozważ użycie tej opcji dla obiektów, takich jak duże strukturami lub tablic, które mogą mieć obciążenie inicjowania.|

- **Atrybuty parametru**

   Tylko ATL interfejsów. Określa, czy parametr jest określony przez **Nazwa parametru** jest **w**, **się**, zarówno lub Brak.

   |Opcja|Opis|
   |------------|-----------------|
   |**in**|Wskazuje, że parametr jest przekazywany z procedury wywołującej do procedury wywoływanej.|
   |**out**|Wskazuje, że parametr wskaźnika jest zwracana z procedury wywoływanej do procedury wywołującej (z serwera do klienta).|

- **Typ parametru**

   Ustawia typ danych parametru. Wybierz typ z listy.

- **Nazwa parametru**

   Ustawia nazwę parametru, którego dodajesz dla właściwości, jeśli właściwość ma następujące parametry. Po kliknięciu **Dodaj**, nazwa parametru jest wyświetlana w **listy parametrów**.

- **Lista parametrów**

   Wyświetla listę atrybutów, które mają zostać dodane do właściwości. Każdy element na liście składa się z nazwy parametru typu parametru i atrybutów. Użyj **Dodaj** i **Usuń** można zaktualizować listy.

- **Add**

   Dodaje parametr należy określić w **Nazwa parametru** i **typ parametru** do **listy parametrów**. Należy kliknąć przycisk **Dodaj** Aby dodać parametr do listy.

- **Usuń**

   Usuwa parametr w **listy parametrów**.

- **Domyślna właściwość**

   Tylko dispinterface MFC. Ustawia tę właściwość jako wartość domyślna dla interfejsu. Interfejs może mieć tylko jedną domyślną właściwości Po określeniu domyślnej właściwości, dla innych właściwości, jeśli są dodawane do interfejsu, to pole jest niedostępne.

## <a name="see-also"></a>Zobacz też

[Dodawanie właściwości](../ide/adding-a-property-visual-cpp.md)<br>
[Atrybuty IDL, Kreator dodawania właściwości](../ide/idl-attributes-add-property-wizard.md)<br>
[Implementowanie interfejsu](../ide/implementing-an-interface-visual-cpp.md)