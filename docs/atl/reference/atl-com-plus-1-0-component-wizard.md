---
title: Kreator 1.0 składnika ATL COM +
ms.date: 10/03/2018
f1_keywords:
- vc.codewiz.class.atl.mts.overview
helpviewer_keywords:
- ATL projects, adding components
- ATL COM+ 1.0 Component Wizard
ms.assetid: 11670681-8671-4122-96a4-2e52f8dadce0
ms.openlocfilehash: 227dda9518b67b410f52db8c6efb33bbc2c8f1b5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50513779"
---
# <a name="atl-com-10-component-wizard"></a>Kreator 1.0 składnika ATL COM +

Użyj tego kreatora, aby dodać obiekt do projektu, który obsługuje usługi COM + 1.0, w tym transakcji.

Można określić, czy obiekt obsługuje podwójne interfejsy i automatyzację. Można również określić obsługę interfejsu informacje o błędzie, formantu rozszerzonego obiektu, transakcji i Kolejkowanie komunikatów asynchronicznych.

> [!WARNING]
> W programie Visual Studio 2017 w wersji 15.9 tego kreatora kodu jest przestarzały i zostanie usunięta w przyszłych wersjach programu Visual Studio. Ten kreator jest rzadko używana. Ogólna obsługa biblioteki ATL i MFC nie ulega zmianie poprzez usunięcie tego kreatora. Jeśli chcesz przekazać opinię dotyczącą tego wycofywania, wypełnij [w ramach tej ankiety](https://www.surveymonkey.com/r/QDWKKCN). Twoja opinia ma znaczenie dla nas.

## <a name="remarks"></a>Uwagi

Począwszy od programu Visual Studio 2008, skrypt rejestrowania generowane przez kreatora, będą rejestrować jego składników modelu COM, w obszarze **HKEY_CURRENT_USER** zamiast **HKEY_LOCAL_MACHINE**. Aby zmienić to zachowanie, ustaw **części rejestru dla wszystkich użytkowników** opcji kreatora ATL.

## <a name="names"></a>Nazwy

Określ nazwy dla obiektu, interfejsów i klas, które mają zostać dodane do projektu. Z wyjątkiem produktów **krótką nazwę**, wszystkie pozostałe pola mogą być edytowane, niezależnie od innych. Jeśli zmienisz tekst **krótką nazwę**, zmiany są widoczne w nazwach wszystkie inne pola na tej stronie. Jeśli zmienisz **Coclass** nazwę w sekcji COM, zmiana jest odzwierciedlana w **typu** i **ProgID** pola, ale **interfejsu** nazwy nie zmienia się. To zachowanie nazewnictwa zaprojektowaną do podejmowania wszystkich nazw można łatwo zidentyfikować dla Ciebie podczas tworzenia kontrolki.

- **Krótka nazwa**

   Ustawia skróconą nazwę dla obiektu. Nazwy, zapewniające Określa `Class` i `Coclass` nazwy, **plik .cpp** i **plik .h klasy** nazwy, **interfejsu** nazwę **Typu** nazwy i **ProgID**, chyba że zmienił się tych pól indywidualnie.

- **plik .h**

   Określa nazwę pliku nagłówkowego klasy nowego obiektu. Domyślnie ta nazwa opiera się na nazwę, która zapewnia w **krótką nazwę**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku na lokalizację lub dołączyć deklaracji klasy do istniejącego pliku. Jeśli wybierzesz istniejący plik, Kreator nie zapisze go w wybranej lokalizacji do momentu kliknij **Zakończ** w kreatorze.

   Kreator nie powoduje zastąpienia pliku. Jeśli wybierasz nazwę istniejącego pliku, po kliknięciu **Zakończ**, Kreator wyświetli monit o wskazują, czy deklaracja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** można dołączyć pliku kliknij przycisk **nie** aby powrócić do kreatora i podaj inną nazwę pliku.

- **Class**

   Ustawia nazwę klasy, która ma zostać utworzony. Ta nazwa jest na podstawie nazwy podane **krótką nazwę**, poprzedzającą "C", typowy prefiks dla nazwy klasy.

- **Plik CPP**

   Określa nazwę pliku implementacji dla nowego obiektu klasy. Domyślnie ta nazwa jest na podstawie nazwy podane **krótką nazwę**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji. Plik nie jest zapisywany w wybranej lokalizacji, dopóki nie klikniesz **Zakończ** w kreatorze.

   Kreator nie powoduje zastąpienia pliku. Jeśli wybierasz nazwę istniejącego pliku, po kliknięciu **Zakończ**, Kreator wyświetli monit o wskazują, czy Implementacja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** można dołączyć pliku kliknij przycisk **nie** aby powrócić do kreatora i podaj inną nazwę pliku.

- **Opartego na atrybutach**

   Wskazuje, czy obiekt używa atrybutów. W przypadku dodawania obiektu do projekcie ATL z atrybutami, ta opcja jest zaznaczone i nie można zmienić. Oznacza to, że można dodać tylko opartego na atrybutach obiekty do projektu utworzonego za pomocą atrybutu pomocy technicznej.

   Jeśli wybierzesz tę opcję, aby Projekt ATL, który nie ma atrybutu pomocy technicznej, w kreatora zostanie wyświetlony monit o określenie, czy chcesz dodać obsługę atrybutu do projektu.

   Wszystkie obiekty, które możesz dodać następujące ustawienie tej opcji są wyznaczone jako opartego na atrybutach domyślnie (pole wyboru jest zaznaczone). Aby wyczyścić to pole, aby dodać obiekt, który nie korzysta z atrybutów.

   Zobacz [ustawienia aplikacji, Kreator projektów ATL](../../atl/reference/application-settings-atl-project-wizard.md) i [podstawowa mechanika atrybutów](../../windows/basic-mechanics-of-attributes.md) Aby uzyskać więcej informacji.

### <a name="com"></a>Model COM

Zawiera informacje dotyczące funkcji COM dla obiektu.

- **Klasa coclass**

   Ustawia nazwę klasy składnika, który zawiera listę interfejsów, obsługiwane przez obiekt.

> [!NOTE]
>  Jeśli tworzysz projekt za pomocą atrybutów lub jeśli na tej stronie kreatora wskazujesz, że składnik COM + 1.0 używa atrybutów, nie można zmienić tej opcji, ponieważ nie ma ATL `coclass` atrybutu.

- **Typ**

   Określa opis obiektu, który będzie wyświetlany w rejestrze

- **Interface**

   Ustawia interfejs, który można utworzyć obiektu. Ten interfejs zawiera swoje niestandardowe metody.

- **Identyfikator programu**

   Ustawia nazwę, która kontenerów można użyć zamiast identyfikatora CLSID obiektu.

## <a name="see-also"></a>Zobacz też

[Składnik ATL COM + 1.0](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)

