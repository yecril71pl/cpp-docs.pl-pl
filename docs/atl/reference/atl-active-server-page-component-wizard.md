---
title: Kreator składników stron ASP ATL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.asp.overview
dev_langs:
- C++
helpviewer_keywords:
- ASP components, creating in ATL
- ATL Active Server Page Component Wizard
ms.assetid: 5a5cb904-dbbf-44ea-ad3d-2ddd14c1d3c5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4d717eefe9c9ee353692d343b88c57469eeb6892
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32359133"
---
# <a name="atl-active-server-page-component-wizard"></a>Kreator składników stron ASP ATL
Ten kreator wstawia w projekcie składnik Active Server Pages (ASP). Microsoft Internet Information Services (IIS) używa składników stron ASP w ramach jego architektury programowanie udoskonalone strony sieci Web.  
  
 Za pomocą tego kreatora, można określić, czy składnik przez wątki modelu i jego obsługa agregacji. Można również określić obsługę interfejsu informacji błąd, punkty połączenia i bezwątkowe przekazywanie.  
  
## <a name="remarks"></a>Uwagi  
 Począwszy od programu Visual Studio 2008 skryptu rejestracji utworzone przez tego kreatora zarejestruje jego składniki modelu COM w obszarze **HKEY_CURRENT_USER** zamiast **HKEY_LOCAL_MACHINE**. Aby zmienić to zachowanie, ustaw **składnik rejestru dla wszystkich użytkowników** opcji kreatora ATL.  
  
## <a name="names"></a>Nazwy  
 Określ nazwy dla obiekt interfejsu i klasy, które mają zostać dodane do projektu. Z wyjątkiem **krótką nazwę**, wszystkie pozostałe pola można edytowane niezależnie od innych. Jeśli zmienisz tekst **krótką nazwę**, znajduje odzwierciedlenie w nazwach wszystkich pól na tej stronie.  
  
 W przypadku zmiany **Coclass** nazwę w sekcji COM, zmiana ta jest uwzględniana w **typu** i **ProgID** pól, ale **interfejsu** nazwy nie zmienia się. To zachowanie nazewnictwa zaprojektowano w celu ułatwić wszystkich nazw identyfikację automatycznie podczas opracowywania formantu.  
  
### <a name="c"></a>C++  
 Informacje dotyczące klasy C++ utworzone dla obiekt.  
  
 **Krótka nazwa**  
 Ustawia nazwę główną dla obiekt. Podane Określa nazwę `Class` i **Coclass** nazwy, **pliku .cpp** i **pliku .h** nazwy, **interfejsu**nazwa **typu** nazwy i **ProgID**, chyba że indywidualnie zmiany tych pól.  
  
 **w pliku .h**  
 Ustawia nazwę pliku nagłówka dla klasy nowego obiektu. Domyślnie ta nazwa jest na podstawie nazwy podanych w **krótką nazwę**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji lub do dołączenia do istniejącego pliku deklaracji klasy. W przypadku wybrania istniejącego pliku, Kreator nie zapisze go w wybranej lokalizacji dopóki kliknij **Zakończ** w kreatorze.  
  
 Kreator nie powoduje zastąpienia pliku. Jeśli po kliknięciu przycisku Wybierz nazwę istniejącego pliku, **Zakończ**, Kreator wyświetli monit, aby wskazać, czy deklaracja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** pliku; kliknij przycisk **nr** aby powrócić do kreatora i podaj inną nazwę pliku.  
  
 **Class**  
 Ustawia nazwę klasy, która ma być utworzony. Ta nazwa jest na podstawie nazwy podanych w **krótką nazwę**, poprzedzającą "C", typowy prefiks nazwy klasy.  
  
 **plik .cpp**  
 Ustawia nazwę pliku implementacji dla nowego obiektu klasy. Domyślnie ta nazwa jest na podstawie nazwy podanych w **krótką nazwę**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji. Plik nie jest zapisywany w wybranej lokalizacji do momentu kliknięcia **Zakończ** w kreatorze.  
  
 Kreator nie powoduje zastąpienia pliku. Jeśli po kliknięciu przycisku Wybierz nazwę istniejącego pliku, **Zakończ**, Kreator wyświetli monit, aby wskazać, czy klasa implementacji powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** pliku; kliknij przycisk **nr** aby powrócić do kreatora i podaj inną nazwę pliku.  
  
 **Atrybut**  
 Wskazuje, czy obiekt używa atrybutów. Jeśli dodajesz obiektu do projekcie ATL z atrybutami, ta opcja jest wybrane i nie można go zmienić. Oznacza to można dodać tylko oparte na atrybutach obiektów do projektu utworzonych za pomocą atrybutu pomocy technicznej.  
  
 Jeśli wybierzesz tę opcję, aby Projekt ATL, który nie ma atrybutu obsługuje, Kreator wyświetli monit Określ, czy dodać atrybut obsługę do projektu.  
  
 Domyślnie dla projektów nonattributed obiekty dodać po ustawieniu tej opcji są oznaczone jako atrybut (pole wyboru jest zaznaczone). Można wyczyść to pole, aby dodać obiekt, który nie używa atrybutów.  
  
 Zobacz [ustawienia aplikacji, Kreator projektu ATL](../../atl/reference/application-settings-atl-project-wizard.md) i [podstawowa mechanika atrybutów](../../windows/basic-mechanics-of-attributes.md) Aby uzyskać więcej informacji.  
  
### <a name="com"></a>Model COM  
 Zawiera informacje o funkcjach COM dla obiekt.  
  
 **Klasa coclass**  
 Ustawia nazwę klasy składnika, który zawiera listę obsługiwanych przez obiekt interfejsów. Jeśli projekt lub ten obiekt używa atrybutów, nie można zmienić tej opcji, ponieważ nie ma ATL **coclass** atrybutu.  
  
 **Typ**  
 Określa opis obiektu, który będzie widoczny w rejestrze dla klasy coclass.  
  
 **Interface**  
 Ustawia interfejs, który można utworzyć obiektu. Ten interfejs zawiera niestandardowej metody.  
  
 **Identyfikator programu**  
 Ustawia nazwę kontenery można użyć zamiast identyfikatora CLSID obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Składnik strony Active Server ATL](../../atl/reference/adding-an-atl-active-server-page-component.md)

