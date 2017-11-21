---
title: Kreator formantu ATL | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.codewiz.class.atl.control.overview
dev_langs: C++
helpviewer_keywords:
- ATL projects, adding controls
- controls [ATL], adding to projects
- ATL Control Wizard
ms.assetid: 991f8e72-ffbc-4382-a4ce-e255acfba5b6
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0b838ac036f6315209b2a4330c120e9c2b7486d6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="atl-control-wizard"></a>Kreator formantu ATL
Wstawia do Projekt ATL (lub projektu MFC z obsługą ATL) formantu ATL. Ten kreator służy do wstawienia jedną z trzech rodzajów kontrolek:  
  
-   Formantu standardowego  
  
-   Złożonych kontrolek  
  
-   DHTML — formant  
  
 Ponadto można określić minimalnej formantu, usunięcie interfejsów z [interfejsów](../../atl/reference/interfaces-atl-control-wizard.md) listy, które są dostarczane jako ustawienia domyślne dla formantów otworzyć w większości kontenerów. Można ustawić interfejsy obsługiwane dla formantu w **interfejsów** stronie kreatora.  
  
## <a name="remarks"></a>Uwagi  
 Utworzone przez tego kreatora skryptu rejestracji zarejestruje jego składniki modelu COM w gałęzi HKEY_CURRENT_USER zamiast HKEY_LOCAL_MACHINE. Aby zmienić to zachowanie, ustaw **składnik rejestru dla wszystkich użytkowników** opcji kreatora ATL.  
  
## <a name="names"></a>Nazwy  
 Określ nazwy dla obiekt interfejsu i klasy, które mają zostać dodane do projektu. Z wyjątkiem **krótką nazwę**, wszystkie pozostałe pola można zmienić niezależnie. Jeśli zmienisz tekst **krótką nazwę**, znajduje odzwierciedlenie w nazwach wszystkich pól na tej stronie. W przypadku zmiany **Coclass** nazwę w sekcji COM, zmiana ta jest uwzględniana w **typu** okno, ale **interfejsu** nazwy i **ProgID** czy Nie zmieniaj. To zachowanie nazewnictwa zaprojektowano w celu ułatwić wszystkich nazw identyfikację automatycznie podczas opracowywania formantu.  
  
> [!NOTE]
>  **Coclass** można edytować tylko nonattributed kontrolek. Jeśli atrybut projektu, nie można edytować **Coclass**.  
  
### <a name="c"></a>C++  
 Informacje dotyczące klasy C++ utworzone w celu implementacji obiektu.  
  
 **Krótka nazwa**  
 Ustawia skróconą nazwę obiektu. Nazwa udostępnianej Określa klasę i **Coclass** nazwy pliku (. CPP i. H) nazw, nazwę interfejsu i **typu** nazw, jeśli nie zmienisz tych pól pojedynczo.  
  
 **Klasy**  
 Ustawia nazwę klasy, która implementuje obiektu. Ta nazwa jest na podstawie nazwy podanych w **krótką nazwę**, poprzedzającą "C", typowy prefiks nazwy klasy.  
  
 **w pliku .h**  
 Ustawia nazwę pliku nagłówka dla klasy nowego obiektu. Domyślnie ta nazwa jest na podstawie nazwy podanych w **krótką nazwę**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji lub do dołączenia do istniejącego pliku deklaracji klasy. W przypadku wybrania istniejącego pliku, Kreator nie zapisze go w wybranej lokalizacji dopóki kliknij **Zakończ**.  
  
 Kreator nie powoduje zastąpienia pliku. Jeśli po kliknięciu przycisku Wybierz nazwę istniejącego pliku, **Zakończ**, Kreator wyświetli monit, aby wskazać, czy deklaracja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** pliku; kliknij przycisk **nr** aby powrócić do kreatora i podaj inną nazwę pliku.  
  
 **plik .cpp**  
 Ustawia nazwę pliku implementacji dla nowego obiektu klasy. Domyślnie ta nazwa jest na podstawie nazwy podanych w **krótką nazwę**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji. Plik nie jest zapisywany w wybranej lokalizacji do momentu kliknięcia **Zakończ** w kreatorze.  
  
 Kreator nie powoduje zastąpienia pliku. Jeśli po kliknięciu przycisku Wybierz nazwę istniejącego pliku, **Zakończ**, Kreator wyświetli monit, aby wskazać, czy klasa implementacji powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** pliku; kliknij przycisk **nr** aby powrócić do kreatora i podaj inną nazwę pliku.  
  
 **Atrybut**  
 Wskazuje, czy obiekt używa atrybutów. Jeśli dodajesz obiektu do projekcie ATL z atrybutami, ta opcja jest wybrane i nie można go zmienić. Oznacza to można dodać tylko oparte na atrybutach obiektów do projektu utworzonych za pomocą atrybutu pomocy technicznej.  
  
 Obiekt oparte na atrybutach można dodać tylko do Projekt ATL, który używa atrybutów. Jeśli wybierzesz tę opcję, aby Projekt ATL, który nie ma atrybutu obsługuje, Kreator wyświetli monit Określ, czy dodać atrybut obsługę do projektu.  
  
 Domyślnie wszystkie obiekty dodać po ustawieniu tej opcji są oznaczone jako atrybut (pole wyboru jest zaznaczone). Można wyczyść to pole, aby dodać obiekt, który nie używa atrybutów.  
  
 Zobacz [ustawienia aplikacji, Kreator projektu ATL](../../atl/reference/application-settings-atl-project-wizard.md) i [podstawowa mechanika atrybutów](../../windows/basic-mechanics-of-attributes.md) Aby uzyskać więcej informacji.  
  
### <a name="com"></a>Model COM  
 Zawiera informacje o funkcjach COM dla obiekt.  
  
 **Klasa coclass**  
 Ustawia nazwę klasy składnika, który zawiera listę obsługiwanych przez obiekt interfejsów.  
  
> [!NOTE]
>  Jeśli tworzysz projekt przy użyciu atrybutów, lub jeśli na tej stronie kreatora wskazaniu, że kontrolka używa atrybutów, nie można zmienić tej opcji, ponieważ nie ma ATL **coclass** atrybutu.  
  
 **Interfejs**  
 Ustawia nazwę interfejsu dla obiektu. Domyślnie nazwa interfejsu jest poprzedzony przez "I".  
  
 **Typ**  
 Określa opis obiektu, który będzie widoczny w rejestrze  
  
 **Identyfikator programu**  
 Ustawia nazwę kontenery można użyć zamiast identyfikatora CLSID obiektu. To pole nie zostanie wypełnione automatycznie. Jeśli to pole nie należy ręcznie wypełniać formantu nie można dostępne dla innych narzędzi. Na przykład formantów ActiveX, które są generowane bez `ProgID` nie są dostępne w **Wstawianie formantu ActiveX** okno dialogowe. Aby uzyskać więcej informacji na temat okna dialogowego, zobacz [okno dialogowe Wstaw formant ActiveX](../../windows/insert-activex-control-dialog-box.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Formant ATL](../../atl/reference/adding-an-atl-control.md)   
 [Dodawanie funkcji do złożonych kontrolek](../../atl/adding-functionality-to-the-composite-control.md)   
 [Podstawowe informacje na temat ATL COM — obiekty](../../atl/fundamentals-of-atl-com-objects.md)

