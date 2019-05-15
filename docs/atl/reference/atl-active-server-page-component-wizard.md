---
title: Kreator składników stron Active Server ATL
ms.date: 05/09/2019
helpviewer_keywords:
- ASP components, creating in ATL
ms.assetid: 5a5cb904-dbbf-44ea-ad3d-2ddd14c1d3c5
ms.openlocfilehash: a78beeab663ef1b467cdec32ca51132e8134a9b2
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707041"
---
# <a name="atl-active-server-page-component-wizard"></a>Kreator składników stron Active Server ATL

::: moniker range="vs-2019"

Ten kreator nie jest dostępne w programie Visual Studio 2019 r i nowszych wersjach.

::: moniker-end

::: moniker range="<=vs-2017"

Ten kreator umożliwia wstawienie do projektu składnika strony Active Server Pages (ASP). Microsoft Internet Information Services (IIS) używa składników ASP jako część jego architekturę rozwoju udoskonalone strony sieci Web.

Za pomocą tego kreatora, można określić, że składnik w wielowątkowości, modelu i jego obsługa agregacji. Można również określić obsługę interfejsu informacje o błędzie, punkty połączenia i bezwątkowy szeregowanie.

## <a name="remarks"></a>Uwagi

Począwszy od programu Visual Studio 2008, skrypt rejestrowania generowane przez ten kreator rejestruje jej składników COM, w obszarze **HKEY_CURRENT_USER** zamiast **HKEY_LOCAL_MACHINE**. Aby zmienić to zachowanie, ustaw **części rejestru dla wszystkich użytkowników** opcji kreatora ATL.

## <a name="names"></a>Nazwy

Określ nazwy dla obiektu, interfejsów i klas, które mają zostać dodane do projektu. Z wyjątkiem **krótką nazwę**, wszystkie pozostałe pola mogą być edytowane, niezależnie od innych. Jeśli zmienisz tekst **krótką nazwę**, zmiany są widoczne w nazwach wszystkie inne pola na tej stronie.

Jeśli zmienisz **Coclass** nazwę w sekcji COM, zmiana jest odzwierciedlana w **typu** i **ProgID** pola, ale **interfejsu** nazwy nie zmienia się. To zachowanie nazewnictwa zaprojektowaną do podejmowania wszystkich nazw można łatwo zidentyfikować dla Ciebie podczas tworzenia kontrolki.

### <a name="c"></a>C++

Zawiera informacje dla klasy języka C++ utworzona dla obiektu.

- **Krótka nazwa**

   Określa nazwę katalogu głównego dla obiektu. Nazwy, zapewniające Określa `Class` i **Coclass** nazwy, **plik .cpp** i **plik .h klasy** nazwy, **interfejsu**nazwy **typu** nazwy i **ProgID**, chyba że zmienił się tych pól indywidualnie.

- **plik .h**

   Określa nazwę pliku nagłówkowego klasy nowego obiektu. Domyślnie ta nazwa opiera się na nazwę, która zapewnia w **krótką nazwę**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku na lokalizację lub dołączyć deklaracji klasy do istniejącego pliku. Jeśli wybierzesz istniejący plik, Kreator nie zapisze go w wybranej lokalizacji do momentu kliknij **Zakończ** w kreatorze.

   Kreator nie powoduje zastąpienia pliku. Jeśli wybierasz nazwę istniejącego pliku, po kliknięciu **Zakończ**, Kreator wyświetli monit o wskazują, czy deklaracja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** można dołączyć pliku kliknij przycisk **nie** aby powrócić do kreatora i podaj inną nazwę pliku.

- **Class**

   Ustawia nazwę klasy, która ma zostać utworzony. Ta nazwa jest oparta na nazwę, która zapewnia w **krótką nazwę**, poprzedzającą "C", typowy prefiks dla nazwy klasy.

- **Plik CPP**

   Określa nazwę pliku implementacji dla nowego obiektu klasy. Domyślnie ta nazwa opiera się na nazwę, która zapewnia w **krótką nazwę**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji. Plik nie jest zapisywany w wybranej lokalizacji, dopóki nie klikniesz **Zakończ** w kreatorze.

   Kreator nie powoduje zastąpienia pliku. Jeśli wybierasz nazwę istniejącego pliku, po kliknięciu **Zakończ**, Kreator wyświetli monit o wskazują, czy Implementacja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** można dołączyć pliku kliknij przycisk **nie** aby powrócić do kreatora i podaj inną nazwę pliku.

- **Opartego na atrybutach**

   Wskazuje, czy obiekt używa atrybutów. W przypadku dodawania obiektu do projekcie ATL z atrybutami, ta opcja jest zaznaczone i nie można zmienić. Oznacza to, że można dodać tylko opartego na atrybutach obiekty do projektu utworzonego za pomocą atrybutu pomocy technicznej.

   Jeśli wybierzesz tę opcję, aby Projekt ATL, który nie ma atrybutu pomocy technicznej, w kreatora zostanie wyświetlony monit o określenie, czy chcesz dodać obsługę atrybutu do projektu.

   Domyślnie w przypadku projektów nonattributed wszystkie obiekty, które możesz dodać po ustawieniu tej opcji są oznaczone jako opartego na atrybutach (pole wyboru jest zaznaczone). Aby wyczyścić to pole, aby dodać obiekt, który nie korzysta z atrybutów.

   Zobacz [ustawienia aplikacji, Kreator projektów ATL](../../atl/reference/application-settings-atl-project-wizard.md) i [podstawowa mechanika atrybutów](../../windows/basic-mechanics-of-attributes.md) Aby uzyskać więcej informacji.

### <a name="com"></a>Model COM

Zawiera informacje dotyczące funkcji COM dla obiektu.

- **Coclass**

   Ustawia nazwę klasy składnika, który zawiera listę interfejsów, obsługiwane przez obiekt. Jeśli projekt lub ten obiekt korzysta z atrybutów, nie można zmienić tej opcji, ponieważ nie ma ATL **coclass** atrybutu.

- **Typ**

   Określa opis obiektu, który będzie wyświetlany w rejestrze dla klasy coclass.

- **Interface**

   Ustawia interfejs, który można utworzyć obiektu. Ten interfejs zawiera swoje niestandardowe metody.

- **ProgID**

   Ustawia nazwę, która kontenerów można użyć zamiast identyfikatora CLSID obiektu.

::: moniker-end

## <a name="see-also"></a>Zobacz także

[Składnika strony Active Server ATL](../../atl/reference/adding-an-atl-active-server-page-component.md)
