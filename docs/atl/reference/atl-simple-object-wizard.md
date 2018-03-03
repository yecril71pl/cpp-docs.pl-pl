---
title: "Kreator prostych obiektów ATL | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.simple.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding objects
- ATL Simple Object Wizard
ms.assetid: f7f85741-9aad-4543-a917-a29b996364da
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cbefa4a8036802599dd97f31d57f18204fd6104f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="atl-simple-object-wizard"></a>Kreator prostych obiektów ATL
Ten kreator wstawia do projektu minimalnego obiektu COM. Ta strona kreatora umożliwia określenie nazwy, które zidentyfikować klasę C++ i pliki dla obiekt i jego funkcje COM.  
  
 Użyj [opcje](../../atl/reference/options-atl-simple-object-wizard.md) strona tego kreatora, aby określić model wątkowości obiektu, jego agregacji obsługuje i czy obsługuje dwa interfejsy i automatyzacji. Można również określić obsługę interfejsu informacji błąd, punkty połączenia, pomocy technicznej programu Internet Explorer i bezwątkowe przekazywanie.  
  
## <a name="remarks"></a>Uwagi  
 Począwszy od programu Visual Studio 2008 skryptu rejestracji utworzone przez tego kreatora zarejestruje jego składniki modelu COM w obszarze **HKEY_CURRENT_USER** zamiast **HKEY_LOCAL_MACHINE**. Aby zmienić to zachowanie, ustaw **składnik rejestru dla wszystkich użytkowników** opcji kreatora ATL.  
  
## <a name="names"></a>Nazwy  
 Określ nazwy dla obiekt interfejsu i klasy, które mają zostać dodane do projektu. Z wyjątkiem **krótką nazwę**, wszystkie pozostałe pola można edytowane niezależnie od innych. Jeśli zmienisz tekst **krótką nazwę**, znajduje odzwierciedlenie w nazwach wszystkich pól na tej stronie. W przypadku zmiany **Coclass** nazwę w sekcji COM, zmiana ta jest uwzględniana w **typu** i **ProgID** pól, ale **interfejsu** nazwy nie zmienia się. To zachowanie nazewnictwa zaprojektowano w celu ułatwić wszystkich nazw identyfikację automatycznie podczas opracowywania formantu.  
  
> [!NOTE]
>  **Coclass** można edytować tylko nonattributed projektów. Jeśli atrybut projektu, nie można edytować **Coclass**.  
  
## <a name="c"></a>C++  
 Informacje dotyczące klasy C++ utworzone dla obiekt.  
  
 **Krótka nazwa**  
 Ustawia skróconą nazwę obiektu. Podane Określa nazwę `Class` i **Coclass** nazwy, **pliku .cpp** i **pliku .h** nazwy, **interfejsu**nazwa **typu** nazwy i **ProgID**, chyba że indywidualnie zmiany tych pól.  
  
 **w pliku .h**  
 Ustawia nazwę pliku nagłówka dla klasy nowego obiektu. Domyślnie ta nazwa jest na podstawie nazwy podanych w **krótką nazwę**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji lub do dołączenia do istniejącego pliku deklaracji klasy. W przypadku wybrania istniejącego pliku, Kreator nie zapisze go w wybranej lokalizacji dopóki kliknij **Zakończ** w kreatorze.  
  
 Kreator nie powoduje zastąpienia pliku. Jeśli po kliknięciu przycisku Wybierz nazwę istniejącego pliku, **Zakończ**, Kreator wyświetli monit, aby wskazać, czy deklaracja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** pliku; kliknij przycisk **nr** aby powrócić do kreatora i podaj inną nazwę pliku.  
  
 **Klasy**  
 Ustawia nazwę klasy, która ma być utworzony. Ta nazwa jest na podstawie nazwy podanych w **krótką nazwę**, poprzedzającą "C", typowy prefiks nazwy klasy.  
  
 **plik .cpp**  
 Ustawia nazwę pliku implementacji dla nowego obiektu klasy. Domyślnie ta nazwa jest na podstawie nazwy podanych w **krótką nazwę**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji. Plik nie jest zapisywany w wybranej lokalizacji do momentu kliknięcia **Zakończ** w kreatorze.  
  
 Kreator nie powoduje zastąpienia pliku. Jeśli po kliknięciu przycisku Wybierz nazwę istniejącego pliku, **Zakończ**, Kreator wyświetli monit, aby wskazać, czy klasa implementacji powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** pliku; kliknij przycisk **nr** aby powrócić do kreatora i podaj inną nazwę pliku.  
  
 **Atrybut**  
 Wskazuje, czy obiekt używa atrybutów. Jeśli dodajesz obiektu do projekcie ATL z atrybutami, ta opcja jest wybrane i nie można go zmienić. Oznacza to można dodać tylko oparte na atrybutach obiektów do projektu utworzonych za pomocą atrybutu pomocy technicznej.  
  
 Obiekt oparte na atrybutach można dodać tylko do Projekt ATL, który używa atrybutów. Jeśli wybierzesz tę opcję, aby Projekt ATL, który nie ma atrybutu obsługuje, Kreator wyświetli monit Określ, czy dodać atrybut obsługę do projektu.  
  
 Domyślnie wszystkie obiekty dodać po ustawieniu tej opcji są oznaczone jako atrybut (pole wyboru jest zaznaczone). Można wyczyść to pole, aby dodać obiekt, który nie używa atrybutów.  
  
 Zobacz [ustawienia aplikacji, Kreator projektu ATL](../../atl/reference/application-settings-atl-project-wizard.md) i [podstawowa mechanika atrybutów](../../windows/basic-mechanics-of-attributes.md) Aby uzyskać więcej informacji.  
  
## <a name="com"></a>Model COM  
 Zawiera informacje o funkcjach COM dla obiekt.  
  
 **Klasa coclass**  
 Ustawia nazwę klasy składnika, który zawiera listę obsługiwanych przez obiekt interfejsów.  
  
> [!NOTE]
>  Jeśli tworzysz projekt przy użyciu atrybutów, lub jeśli na tej stronie kreatora wskazaniu, że obiekt używa atrybutów, nie można zmienić tej opcji, ponieważ nie ma ATL `coclass` atrybutu.  
  
 **Typ**  
 Określa opis obiektu, który będzie widoczny w rejestrze  
  
 **Interfejs**  
 Ustawia interfejs, który można utworzyć obiektu. Ten interfejs zawiera niestandardowej metody.  
  
 **Identyfikator programu**  
 Ustawia nazwę kontenery można użyć zamiast identyfikatora CLSID obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Prosty obiekt ATL](../../atl/reference/adding-an-atl-simple-object.md)

