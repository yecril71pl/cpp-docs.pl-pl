---
title: Kreator prostych obiektów ATL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.simple.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding objects
- ATL Simple Object Wizard
ms.assetid: f7f85741-9aad-4543-a917-a29b996364da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6d2af751a136416934f378b41bed11b1aa74ad80
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37883495"
---
# <a name="atl-simple-object-wizard"></a>Kreator prostych obiektów ATL
Ten kreator wstawia do projektu obiekt COM minimalny. Ta strona kreatora umożliwia określenie nazwy, które identyfikują klasy języka C++ i pliki dla obiektu i jego funkcje COM.  
  
 Użyj [opcje](../../atl/reference/options-atl-simple-object-wizard.md) obsługuje stronach tego kreatora, aby określić model wątkowości obiektu, jego agregacji i tego, czy obsługuje podwójne interfejsy i automatyzację. Można również określić obsługę interfejsu informacje o błędzie, punkty połączenia, pomocy technicznej programu Internet Explorer i bezwątkowy szeregowanie.  
  
## <a name="remarks"></a>Uwagi  
 Począwszy od programu Visual Studio 2008, skrypt rejestrowania generowane przez kreatora, będą rejestrować jego składników modelu COM, w obszarze **HKEY_CURRENT_USER** zamiast **HKEY_LOCAL_MACHINE**. Aby zmienić to zachowanie, ustaw **części rejestru dla wszystkich użytkowników** opcji kreatora ATL.  
  
## <a name="names"></a>Nazwy  
 Określ nazwy dla obiektu, interfejsów i klas, które mają zostać dodane do projektu. Z wyjątkiem **krótką nazwę**, wszystkie pozostałe pola mogą być edytowane, niezależnie od innych. Jeśli zmienisz tekst **krótką nazwę**, zmiany są widoczne w nazwach wszystkie inne pola na tej stronie. Jeśli zmienisz **Coclass** nazwę w sekcji COM, zmiana jest odzwierciedlana w **typu** i **ProgID** pola, ale **interfejsu** nazwy nie zmienia się. To zachowanie nazewnictwa zaprojektowaną do podejmowania wszystkich nazw można łatwo zidentyfikować dla Ciebie podczas tworzenia kontrolki.  
  
> [!NOTE]
>  **Klasa coclass** można edytować tylko nonattributed projektów. Jeśli projekt jest przypisane, nie można edytować **Coclass**.  
  
## <a name="c"></a>C++  
 Zawiera informacje dla klasy języka C++ utworzona dla obiektu.  
  
 **Krótka nazwa**  
 Ustawia skróconą nazwę dla obiektu. Nazwy, zapewniające Określa `Class` i `Coclass` nazwy, **plik .cpp** i **plik .h klasy** nazwy, **interfejsu** nazwę **Typu** nazwy i **ProgID**, chyba że zmienił się tych pól indywidualnie.  
  
 **plik .h**  
 Określa nazwę pliku nagłówkowego klasy nowego obiektu. Domyślnie ta nazwa opiera się na nazwę, która zapewnia w **krótką nazwę**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku na lokalizację lub dołączyć deklaracji klasy do istniejącego pliku. Jeśli wybierzesz istniejący plik, Kreator nie zapisze go w wybranej lokalizacji do momentu kliknij **Zakończ** w kreatorze.  
  
 Kreator nie powoduje zastąpienia pliku. Jeśli wybierasz nazwę istniejącego pliku, po kliknięciu **Zakończ**, Kreator wyświetli monit o wskazują, czy deklaracja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** można dołączyć pliku kliknij przycisk **nie** aby powrócić do kreatora i podaj inną nazwę pliku.  
  
 **Class**  
 Ustawia nazwę klasy, która ma zostać utworzony. Ta nazwa jest oparta na nazwę, która zapewnia w **krótką nazwę**, poprzedzającą "C", typowy prefiks dla nazwy klasy.  
  
 **Plik CPP**  
 Określa nazwę pliku implementacji dla nowego obiektu klasy. Domyślnie ta nazwa opiera się na nazwę, która zapewnia w **krótką nazwę**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji. Plik nie jest zapisywany w wybranej lokalizacji, dopóki nie klikniesz **Zakończ** w kreatorze.  
  
 Kreator nie powoduje zastąpienia pliku. Jeśli wybierasz nazwę istniejącego pliku, po kliknięciu **Zakończ**, Kreator wyświetli monit o wskazują, czy Implementacja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** można dołączyć pliku kliknij przycisk **nie** aby powrócić do kreatora i podaj inną nazwę pliku.  
  
 **Opartego na atrybutach**  
 Wskazuje, czy obiekt używa atrybutów. W przypadku dodawania obiektu do projekcie ATL z atrybutami, ta opcja jest zaznaczone i nie można zmienić. Oznacza to, że można dodać tylko opartego na atrybutach obiekty do projektu utworzonego za pomocą atrybutu pomocy technicznej.  
  
 Obiekt opartego na atrybutach można dodać tylko do projektu ATL, który używa atrybutów. Jeśli wybierzesz tę opcję, aby Projekt ATL, który nie ma atrybutu pomocy technicznej, w kreatora zostanie wyświetlony monit o określenie, czy chcesz dodać obsługę atrybutu do projektu.  
  
 Domyślnie wszystkie obiekty, które możesz dodać po ustawieniu tej opcji są oznaczone jako opartego na atrybutach (pole wyboru jest zaznaczone). Aby wyczyścić to pole, aby dodać obiekt, który nie korzysta z atrybutów.  
  
 Zobacz [ustawienia aplikacji, Kreator projektów ATL](../../atl/reference/application-settings-atl-project-wizard.md) i [podstawowa mechanika atrybutów](../../windows/basic-mechanics-of-attributes.md) Aby uzyskać więcej informacji.  
  
## <a name="com"></a>Model COM  
 Zawiera informacje dotyczące funkcji COM dla obiektu.  
  
 **Klasa coclass**  
 Ustawia nazwę klasy składnika, który zawiera listę interfejsów, obsługiwane przez obiekt.  
  
> [!NOTE]
>  Jeśli tworzysz projekt za pomocą atrybutów lub jeśli na tej stronie kreatora wskazujesz, że obiekt używa atrybutów, nie można zmienić tej opcji, ponieważ nie ma ATL `coclass` atrybutu.  
  
 **Typ**  
 Określa opis obiektu, który będzie wyświetlany w rejestrze  
  
 **Interface**  
 Ustawia interfejs, który można utworzyć obiektu. Ten interfejs zawiera swoje niestandardowe metody.  
  
 **Identyfikator programu**  
 Ustawia nazwę, która kontenerów można użyć zamiast identyfikatora CLSID obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Prosty obiekt ATL](../../atl/reference/adding-an-atl-simple-object.md)

