---
title: "Kreator strony właściwości ATL | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.codewiz.class.atl.ppg.overview
dev_langs: C++
helpviewer_keywords:
- ATL projects, adding property pages
- ATL Property Page Wizard
ms.assetid: 6113e325-facd-4f68-b491-144d75209922
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: eaab86ab72ef41bfe97a67c6d8845e8ce3d3c899
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="atl-property-page-wizard"></a>Kreator strony właściwości ATL
Ten kreator [dodaje do projektu ATL strony właściwości](../../atl/reference/adding-an-atl-property-page.md) lub do projektu MFC z obsługą ATL. Strony właściwości ATL udostępnia interfejs użytkownika do ustawiania właściwości (lub wywołanie metody) jeden lub więcej obiektów COM.  
  
## <a name="remarks"></a>Uwagi  
 Począwszy od programu Visual Studio 2008 skryptu rejestracji utworzone przez tego kreatora zarejestruje jego składniki modelu COM w obszarze **HKEY_CURRENT_USER** zamiast **HKEY_LOCAL_MACHINE**. Aby zmienić to zachowanie, ustaw **składnik rejestru dla wszystkich użytkowników** opcji kreatora ATL.  
  
## <a name="names"></a>Nazwy  
 Określ nazwy dla obiekt interfejsu i klasy, które mają zostać dodane do projektu. Z wyjątkiem **krótką nazwę**, wszystkie pozostałe pola, które mogą być edytowane niezależnie. Jeśli zmienisz tekst **krótką nazwę**, znajduje odzwierciedlenie w nazwach wszystkich pól na tej stronie. Jeśli zmienisz **Coclass** nazwę w sekcji COM, zmiana ta jest uwzględniana w **typu** i **ProgID** pola. To zachowanie nazewnictwa zaprojektowano w celu ułatwić wszystkich nazw identyfikację automatycznie podczas opracowywania stronę właściwości.  
  
> [!NOTE]
>  **Coclass** można edytować tylko nonattributed projektów. Jeśli atrybut projektu, nie można edytować **Coclass**.  
  
### <a name="c"></a>C++  
 Informacje dotyczące klasy C++ utworzone w celu implementacji obiektu.  
  
|||  
|-|-|  
|Termin|Definicja|  
|**Krótka nazwa**|Ustawia skróconą nazwę obiektu. Nazwa udostępnianej Określa klasę i **Coclass** nazwy pliku (**.cpp** i **.h**) nazw, **typu** nazwy i  **ProgID**, chyba że indywidualnie zmiany tych pól.|  
|**w pliku .h**|Ustawia nazwę pliku nagłówka dla klasy nowego obiektu. Domyślnie ta nazwa jest na podstawie nazwy podanych w **krótką nazwę**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji lub do dołączenia do istniejącego pliku deklaracji klasy. W przypadku wybrania istniejącego pliku, Kreator nie zapisze go w wybranej lokalizacji dopóki kliknij **Zakończ** w kreatorze.<br /><br /> Kreator nie powoduje zastąpienia pliku. Jeśli po kliknięciu przycisku Wybierz nazwę istniejącego pliku, **Zakończ**, Kreator wyświetli monit, aby wskazać, czy deklaracja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** pliku; kliknij przycisk **nr** aby powrócić do kreatora i podaj inną nazwę pliku.|  
|**Klasy**|Ustawia nazwę klasy, która implementuje obiektu. Ta nazwa jest na podstawie nazwy podanych w **krótką nazwę**, poprzedzającą "C", typowy prefiks nazwy klasy.|  
|**plik .cpp**|Ustawia nazwę pliku implementacji dla nowego obiektu klasy. Domyślnie ta nazwa jest na podstawie nazwy podanych w **krótką nazwę**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji. Plik nie jest zapisywany w wybranej lokalizacji do momentu kliknięcia **Zakończ** w kreatorze.<br /><br /> Kreator nie powoduje zastąpienia pliku. Jeśli po kliknięciu przycisku Wybierz nazwę istniejącego pliku, **Zakończ**, Kreator wyświetli monit, aby wskazać, czy klasa implementacji powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** pliku; kliknij przycisk **nr** aby powrócić do kreatora i podaj inną nazwę pliku.|  
|**Atrybut**|Wskazuje, czy obiekt używa atrybutów. Jeśli obiekt jest dodawany do projekcie ATL z atrybutami, ta opcja jest zaznaczona i nie można zmienić, oznacza to, można dodać tylko przypisane obiekty do projektu utworzonych za pomocą atrybutu pomocy technicznej.<br /><br /> Obiekt oparte na atrybutach można dodać tylko do Projekt ATL, który używa atrybutów. Jeśli wybierzesz tę opcję, aby Projekt ATL, który nie ma atrybutu obsługuje, Kreator wyświetli monit Określ, czy dodać atrybut obsługę do projektu.<br /><br /> Domyślnie wszystkie obiekty dodać po ustawieniu tej opcji są oznaczone jako atrybut (pole wyboru jest zaznaczone). Można wyczyść to pole, aby dodać obiekt, który nie używa atrybutów.<br /><br /> Zobacz [ustawienia aplikacji, Kreator projektu ATL](../../atl/reference/application-settings-atl-project-wizard.md) i [podstawowa mechanika atrybutów](../../windows/basic-mechanics-of-attributes.md) Aby uzyskać więcej informacji.|  
  
### <a name="com"></a>Model COM  
 Zawiera informacje o funkcjach COM dla obiekt.  
  
 **Klasa coclass**  
 Ustawia nazwę klasy składnika, który zawiera listę obsługiwanych przez obiekt interfejsów.  
  
> [!NOTE]
>  Jeśli tworzysz projekt przy użyciu atrybutów, lub jeśli na tej stronie kreatora wskazaniu, że strona właściwości używa atrybutów, nie można zmienić tej opcji, ponieważ nie ma ATL `coclass` atrybutu.  
  
 **Typ**  
 Określa opis obiektu, który będzie widoczny w rejestrze  
  
 **Identyfikator programu**  
 Ustawia nazwę kontenery można użyć zamiast identyfikatora CLSID obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje, Kreator strony właściwości ATL](../../atl/reference/options-atl-property-page-wizard.md)   
 [Ciągi, Kreator strony właściwości ATL](../../atl/reference/strings-atl-property-page-wizard.md)   
 [Przykład: Implementacja strony właściwości](../../atl/example-implementing-a-property-page.md)

