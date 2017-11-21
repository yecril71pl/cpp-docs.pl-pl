---
title: "ATL COM + 1.0 Kreator składników stron ASP | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.codewiz.class.atl.mts.overview
dev_langs: C++
helpviewer_keywords:
- ATL projects, adding components
- ATL COM+ 1.0 Component Wizard
ms.assetid: 11670681-8671-4122-96a4-2e52f8dadce0
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d7d596396ec46aa1f30be00743ab6fe95d49a865
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="atl-com-10-component-wizard"></a>ATL COM + 1.0 Kreator składników stron ASP
Użyj tego kreatora można dodać obiektu do projektu obsługującego usług COM + 1.0, w tym transakcji.  
  
 Można określić, czy obiekt obsługuje dwa interfejsy i automatyzacji. Można również określić obsługę interfejsu informacji błąd, formantu rozszerzonego obiektu, transakcji i usługi kolejkowania komunikatów asynchronicznych.  
  
## <a name="remarks"></a>Uwagi  
 Począwszy od programu Visual Studio 2008 skryptu rejestracji utworzone przez tego kreatora zarejestruje jego składniki modelu COM w obszarze **HKEY_CURRENT_USER** zamiast **HKEY_LOCAL_MACHINE**. Aby zmienić to zachowanie, ustaw **składnik rejestru dla wszystkich użytkowników** opcji kreatora ATL.  
  
## <a name="names"></a>Nazwy  
 Określ nazwy dla obiekt interfejsu i klasy, które mają zostać dodane do projektu. Z wyjątkiem produktów **krótką nazwę**, wszystkie pozostałe pola można edytowane niezależnie od innych. Jeśli zmienisz tekst **krótką nazwę**, znajduje odzwierciedlenie w nazwach wszystkich pól na tej stronie. W przypadku zmiany **Coclass** nazwę w sekcji COM, zmiana ta jest uwzględniana w **typu** i **ProgID** pól, ale **interfejsu** nazwy nie zmienia się. To zachowanie nazewnictwa zaprojektowano w celu ułatwić wszystkich nazw identyfikację automatycznie podczas opracowywania formantu.  
  
 **Krótka nazwa**  
 Ustawia skróconą nazwę obiektu. Podane Określa nazwę `Class` i `Coclass` nazwy, **pliku .cpp** i **pliku .h** nazwy, **interfejsu** name, **Typu** nazwy i **ProgID**, chyba że indywidualnie zmiany tych pól.  
  
 **w pliku .h**  
 Ustawia nazwę pliku nagłówka dla klasy nowego obiektu. Domyślnie ta nazwa jest na podstawie nazwy podanych w **krótką nazwę**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji lub do dołączenia do istniejącego pliku deklaracji klasy. Jeśli wybierzesz istniejący plik, Kreator nie zapisze go w wybranej lokalizacji dopóki kliknij **Zakończ** w kreatorze.  
  
 Kreator nie powoduje zastąpienia pliku. Jeśli po kliknięciu przycisku Wybierz nazwę istniejącego pliku, **Zakończ**, Kreator wyświetli monit, aby wskazać, czy deklaracja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** pliku; kliknij przycisk **nr** aby powrócić do kreatora i podaj inną nazwę pliku.  
  
 **Klasy**  
 Ustawia nazwę klasy, która ma być utworzony. Ta nazwa jest na podstawie nazwy podane **krótką nazwę**, poprzedzającą "C", typowy prefiks nazwy klasy.  
  
 **plik .cpp**  
 Ustawia nazwę pliku implementacji dla nowego obiektu klasy. Domyślnie ta nazwa jest na podstawie nazwy podane **krótką nazwę**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji. Plik nie jest zapisywany w wybranej lokalizacji do momentu kliknięcia **Zakończ** w kreatorze.  
  
 Kreator nie powoduje zastąpienia pliku. Jeśli po kliknięciu przycisku Wybierz nazwę istniejącego pliku, **Zakończ**, Kreator wyświetli monit, aby wskazać, czy klasa implementacji powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** pliku; kliknij przycisk **nr** aby powrócić do kreatora i podaj inną nazwę pliku.  
  
 **Atrybut**  
 Wskazuje, czy obiekt używa atrybutów. Jeśli dodajesz obiektu do projekcie ATL z atrybutami, ta opcja jest wybrane i nie można go zmienić. Oznacza to można dodać tylko oparte na atrybutach obiektów do projektu utworzonych za pomocą atrybutu pomocy technicznej.  
  
 Jeśli wybierzesz tę opcję, aby Projekt ATL, który nie ma atrybutu obsługuje, Kreator wyświetli monit Określ, czy dodać atrybut obsługę do projektu.  
  
 Wszystkie obiekty, należy dodać następujące ustawienie dla tej opcji są wyznaczone jako atrybut domyślnie (pole wyboru jest zaznaczone). Można wyczyść to pole, aby dodać obiekt, który nie używa atrybutów.  
  
 Zobacz [ustawienia aplikacji, Kreator projektu ATL](../../atl/reference/application-settings-atl-project-wizard.md) i [podstawowa mechanika atrybutów](../../windows/basic-mechanics-of-attributes.md) Aby uzyskać więcej informacji.  
  
### <a name="com"></a>Model COM  
 Zawiera informacje o funkcjach COM dla obiekt.  
  
 **Klasa coclass**  
 Ustawia nazwę klasy składnika, który zawiera listę obsługiwanych przez obiekt interfejsów.  
  
> [!NOTE]
>  Jeśli tworzysz projekt przy użyciu atrybutów, lub jeśli na tej stronie kreatora wskazaniu, że składnik COM + 1.0 używa atrybutów, nie można zmienić tej opcji, ponieważ nie ma ATL `coclass` atrybutu.  
  
 **Typ**  
 Określa opis obiektu, który będzie widoczny w rejestrze  
  
 **Interfejs**  
 Ustawia interfejs, który można utworzyć obiektu. Ten interfejs zawiera niestandardowej metody.  
  
 **Identyfikator programu**  
 Ustawia nazwę kontenery można użyć zamiast identyfikatora CLSID obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Składnik ATL COM + 1.0](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)

