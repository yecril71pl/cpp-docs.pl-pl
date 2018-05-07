---
title: Nazwy, Dodaj Kreatora właściwości | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 17c3fd5cfc86f76fcdc1c301bd92bb1fdfac3b9c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="names-add-property-wizard"></a>Nazwy, Dodaj kreatora właściwości
Ten kreator umożliwia dodawanie właściwości do interfejsu.  
  
 **Typ właściwości**  
 Ustawia typ właściwości, który dodajesz. Podaj własny typ lub wybierz z listy wstępnie zdefiniowanych MFC dispinterfaces. Jeśli podasz standardowych implementacji właściwości, **typ właściwości** ma ustawioną wartość typu podstawowego i jest niedostępna w przypadku zmiany.  
  
 **Nazwa właściwości**  
 Ustawia nazwę właściwości. Dla dispinterfaces MFC związane z formantami ActiveX możesz podać własną nazwę lub nazwę właściwości standardowych można wybrać z listy wstępnie zdefiniowanych. Jeśli podasz z własnej nazwy właściwości **giełdowych** typ implementacji jest niedostępny. Zobacz [właściwości zasobu](../ide/stock-properties.md) opis właściwości na liście.  
  
|Typ interfejsu|Opis|  
|--------------------|-----------------|  
|Interfejs podwójny ATL, niestandardowy interfejs i lokalne niestandardowy interfejs|Podaj nazwę właściwości.|  
|Dispinterface MFC, dispinterface kontrolki MFC ActiveX|Podaj nazwę właściwości lub wybierz z listy właściwości standardowych. Jeśli wybierzesz właściwość z listy odpowiednią wartość znajduje się w **typ właściwości** pola. Można zmienić tego typu, w zależności od dokonanego w obszarze **typ implementacji**.|  
  
 **Zwracany typ**  
 Tylko ATL interfejsów. Ustawia typ zwrotny dla właściwości. W przypadku dwóch interfejsów `HRESULT` zawsze jest zwracany typ i to pole jest niedostępne. W przypadku niestandardowych interfejsów zwracanego typu można wybrać z listy. `HRESULT` nadal zaleca się, ponieważ zapewnia standardowy sposób zwracać błędów.  
  
 **Nazwa zmiennej**  
 Tylko dispinterfaces MFC. Dostępne tylko w przypadku określenia **zmiennej członkowskiej** w obszarze **typ implementacji**. Ustawia nazwę zmiennej członkowskiej, z którym jest skojarzona właściwość. Domyślnie, nazwa zmiennej jest ustawiona wartość m_*PropertyName*. Można edytować tej nazwy.  
  
 **Funkcja powiadomień**  
 Tylko dispinterfaces MFC. Dostępne tylko w przypadku określenia **zmiennej członkowskiej** w obszarze **typ implementacji**. Ustawia nazwę Jeśli wywołana funkcja powiadomień zmiany właściwości. Domyślnie nazwa funkcji powiadomień jest ustawiona na*PropertyName*zmienione. Można edytować tej nazwy.  
  
 **Funkcja Get**  
 Dla MFC dispinterfaces. Dostępne tylko w przypadku określenia **metod Get/Set** w obszarze **typ implementacji**. Ustawia nazwę funkcji do pobrania właściwości. Nazwa funkcji Get jest domyślnie GET*PropertyName*. Można edytować tej nazwy. Jeśli nazwa funkcji [GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported) są wstawiane do mapy interfejsu wysyłania. Pobierz*PropertyName* funkcji określa, że właściwość jako czytelna.  
  
 **Set — funkcja**  
 Tylko dispinterfaces MFC. Dostępne tylko w przypadku określenia **metod Get/Set** w obszarze **typ implementacji**. Ustawia nazwę funkcji, które można ustawić właściwości. Domyślnie, nazwa zestawu funkcji ustawiono zestawu*PropertyName*. Można edytować tej nazwy. Jeśli nazwa funkcji [SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported) są wstawiane do mapy interfejsu wysyłania. Zestaw*PropertyName* funkcji określa, czy właściwość jest zapisywalna.  
  
 **Typ implementacji**  
 Tylko dispinterfaces MFC. Określa sposób implementuje właściwości, który dodajesz.  
  
|Typ implementacji|Opis|  
|-------------------------|-----------------|  
|**Zapasów**|Określa podstawowe implementacji dla właściwości wybranego w **nazwa właściwości**. Domyślnie. Zobacz [właściwości zasobu](../ide/stock-properties.md) Aby uzyskać więcej informacji.<br /><br /> Jeśli określisz **giełdowych**, następnie **typ właściwości**, **typ parametru**, i **Nazwa parametru** są niedostępne.|  
|**Zmiennej członkowskiej**|Określa, że właściwość nie zostanie dodany jako zmienną członkowską. Zmienne członkowskie można dodać właściwości niestandardowe lub większość standardowych właściwości. Nie można określić **zmiennej członkowskiej** dla **podpis**, **hWnd**, i **tekst** właściwości.<br /><br /> Udostępnia domyślne nazwy w obszarze **nazwa zmiennej** i **funkcję powiadomień**. Można edytować tej nazwy.|  
|**Pobierz/Ustaw metody**|Określa właściwość jest dodawany jako Get*PropertyName* i*PropertyName* funkcje domyślnie. Te nazwy są wyświetlane w polu **Get — funkcja** i **Set — funkcja**.<br /><br /> Możesz zmienić domyślną **typ właściwości**, która przekazuje wartość funkcji Get. Można określić parametrów **uzyskać** i `Set` funkcji.|  
  
 **Funkcja Get**  
 Na ALT interfejsów. Ustawia właściwość jako czytelna; oznacza to, tworzy **uzyskać** metodę pobierania tej właściwości z obiektu. Musisz wybrać **uzyskać**, `Put`, lub obie.  
  
 **Put — funkcja**  
 Tylko ATL interfejsów. Ustawia właściwość zapisywalny; oznacza to, tworzy `Put` metoda ustawienie lub "wprowadzenie", ta właściwość obiektu. Musisz wybrać **uzyskać**, `Put`, lub obie. Jeśli wybierzesz tę opcję, są dostępne dwa sposoby implementacji metody:  
  
|Opcja|Opis|  
|------------|-----------------|  
|**PropPut**|[PropPut](../windows/propput.md) funkcja zwraca kopię obiektu. Jest to wartość domyślna i najczęściej do zapisu właściwości.|  
|**PropPutRef**|[PropPutRef](../windows/propputref.md) funkcja zwraca odwołanie do obiektu, a nie zwracających kopię samego obiektu. Rozważ użycie tej opcji dla obiektów, takich jak duże struktury lub tablic, mających koszty inicjowania.|  
  
 **Atrybuty parametrów**  
 Tylko ATL interfejsów. Określa, czy parametr jest określony przez **Nazwa parametru** jest **w**, **limit**, zarówno lub none.  
  
|Opcja|Opis|  
|------------|-----------------|  
|**in**|Wskazuje, że parametr jest przekazywany z procedury wywołującej do procedury wywoływanej.|  
|**out**|Wskazuje, że parametr wskaźnika jest zwracana z procedury wywoływanej do procedury wywołującej (z serwera do klienta).|  
  
 **Typ parametru**  
 Ustawia typ danych parametru. Wybierz typ z listy.  
  
 **Nazwa parametru**  
 Ustawia nazwę parametru dodawanego do właściwości, jeśli właściwość ma następujące parametry. Po kliknięciu **Dodaj**, nazwa parametru jest wyświetlana w **listy parametrów**.  
  
 **Listy parametrów**  
 Wyświetla listę atrybutów, które mają zostać dodane do właściwości. Każdy element na liście składa się z nazwy parametru typu parametru i atrybutów. Użyj **Dodaj** i **Usuń** Aby zaktualizować listę.  
  
 **Dodaj**  
 Dodaje parametr należy określić w **Nazwa parametru** i **typ parametru** do **listy parametrów**. Należy kliknąć opcję **Dodaj** powoduje dodanie parametru do listy.  
  
 **Usuń**  
 Usuwa parametr należy wybrać w **listy parametrów**.  
  
 **Właściwości domyślne**  
 Tylko dispinterface MFC. Ustawia tę właściwość jako domyślny dla interfejsu. Interfejs może mieć tylko jedną domyślną właściwość; Po określeniu właściwością domyślną dla innych właściwości dodawany do interfejsu, to pole jest niedostępne.  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie właściwości](../ide/adding-a-property-visual-cpp.md)   
 [Atrybuty IDL, Dodaj Kreatora właściwości](../ide/idl-attributes-add-property-wizard.md)   
 [Implementowanie interfejsu](../ide/implementing-an-interface-visual-cpp.md)