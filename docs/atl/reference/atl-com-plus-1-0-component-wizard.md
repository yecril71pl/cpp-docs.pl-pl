---
title: Kreator składników ATL COM+ 1.0
ms.date: 05/08/2019
helpviewer_keywords:
- ATL projects, adding components
ms.assetid: 11670681-8671-4122-96a4-2e52f8dadce0
ms.openlocfilehash: 6b1fea925c5f6d657e398933b5fb26cf09c28055
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2020
ms.locfileid: "91353158"
---
# <a name="atl-com-10-component-wizard"></a>Kreator składników ATL COM+ 1.0

::: moniker range="vs-2019"

Ten Kreator nie jest dostępny w programie Visual Studio 2019 i nowszych.

::: moniker-end

::: moniker range="<=vs-2017"

Użyj tego kreatora, aby dodać obiekt do projektu, który obsługuje usługi modelu COM+ 1,0, w tym transakcje.

Można określić, czy obiekt obsługuje podwójne interfejsy i automatyzację. Możesz również wskazać obsługę interfejsu informacji o błędach, ulepszonej kontrolce obiektu, transakcji i asynchronicznej usługi kolejkowania komunikatów.

## <a name="remarks"></a>Uwagi

Począwszy od programu Visual Studio 2008 skrypt rejestracji utworzony przez tego kreatora spowoduje zarejestrowanie jego składników modelu COM w **HKEY_CURRENT_USER** , a nie **HKEY_LOCAL_MACHINE**. Aby zmienić to zachowanie, ustaw opcję **Zarejestruj składnik dla wszystkich użytkowników** w Kreatorze ATL.

## <a name="names"></a>Nazwy

Określ nazwy obiektu, interfejsu i klas, które mają zostać dodane do projektu. Z wyjątkiem **krótkiej nazwy**wszystkie inne pola można edytować niezależnie od innych. Jeśli zmienisz tekst **skróconej nazwy**, zmiana zostanie odzwierciedlona w nazwach wszystkich innych pól na tej stronie. Jeśli zmienisz nazwę **klasy coclass** w sekcji com, zmiana zostanie odzwierciedlona w polach **Typ** i **ProgID** , ale nazwa **interfejsu** nie zostanie zmieniona. Takie zachowanie nazewnictwa zostało zaprojektowane, aby wszystkie nazwy były łatwo rozpoznawalne podczas tworzenia kontrolki.

- **Krótka nazwa**

   Ustawia skróconą nazwę obiektu. Nazwa dostarczana przez użytkownika określa nazwy `Class` i nazwy `Coclass` plików **. cpp** oraz **. h** , nazwę **interfejsu** , nazwy **typów** i **Identyfikator ProgID**, chyba że te pola są zmieniane pojedynczo.

- **plik h**

   Ustawia nazwę pliku nagłówka dla klasy nowego obiektu. Domyślnie ta nazwa jest oparta na nazwie podanym w polu **krótka nazwa**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji, lub dołączyć deklarację klasy do istniejącego pliku. Jeśli wybierzesz istniejący plik, Kreator nie zapisze go w wybranej lokalizacji, dopóki nie klikniesz przycisku **Zakończ** w kreatorze.

   Kreator nie zastępuje pliku. Jeśli wybierzesz nazwę istniejącego pliku, po kliknięciu przycisku **Zakończ**Kreator monituje o wskazanie, czy deklaracja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** , aby dołączyć plik; Kliknij przycisk **nie** , aby powrócić do kreatora i określić inną nazwę pliku.

- **Klasa**

   Ustawia nazwę klasy, która ma zostać utworzona. Ta nazwa jest oparta na nazwie podanym w **skrócie nazwa**, poprzedzona znakiem "C", typowym prefiksem dla nazwy klasy.

- **plik. cpp**

   Ustawia nazwę pliku implementacji dla klasy nowego obiektu. Domyślnie ta nazwa jest oparta na nazwie podanym w polu **krótka nazwa**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji. Plik nie jest zapisywany w wybranej lokalizacji, dopóki nie zostanie kliknięty przycisk **Zakończ** w kreatorze.

   Kreator nie zastępuje pliku. W przypadku wybrania nazwy istniejącego pliku po kliknięciu przycisku **Zakończ**Kreator monituje o wskazanie, czy implementacja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** , aby dołączyć plik; Kliknij przycisk **nie** , aby powrócić do kreatora i określić inną nazwę pliku.

- **Przypisanych**

   Wskazuje, czy obiekt używa atrybutów. Jeśli dodajesz obiekt do projektu ATL z atrybutami, ta opcja jest zaznaczona i nie można jej zmienić. Oznacza to, że można dodawać tylko obiekty z atrybutami do projektu utworzonego za pomocą obsługi atrybutu.

   W przypadku wybrania tej opcji dla projektu ATL, który nie obsługuje atrybutu, Kreator poprosi o określenie, czy chcesz dodać obsługę atrybutu do projektu.

   Wszystkie obiekty dodane po ustawieniu tej opcji są oznaczone domyślnie jako przypisane do atrybutu (pole wyboru jest zaznaczone). Możesz wyczyścić to pole, aby dodać obiekt, który nie używa atrybutów.

   Aby uzyskać więcej informacji [, zobacz Ustawienia aplikacji, Kreator projektu ATL](../../atl/reference/application-settings-atl-project-wizard.md) i [podstawowe Mechanics atrybutów](../../windows/attributes/cpp-attributes-com-net.md#basic-mechanics-of-attributes) .

### <a name="com"></a>Model COM

Zawiera informacje o funkcji COM dla obiektu.

- **Klasa coclass**

   Ustawia nazwę klasy składnika, która zawiera listę interfejsów obsługiwanych przez obiekt.

> [!NOTE]
> Jeśli tworzysz projekt przy użyciu atrybutów lub w przypadku wybrania na tej stronie kreatora, że składnik COM+ 1,0 używa atrybutów, nie można zmienić tej opcji, ponieważ ATL nie zawiera `coclass` atrybutu.

- **Typ**

   Ustawia opis obiektu, który będzie wyświetlany w rejestrze

- **Interfejs**

   Ustawia interfejs tworzony dla obiektu. Ten interfejs zawiera własne metody.

- **ProgID**

   Ustawia nazwę, która może być używana przez kontenery zamiast identyfikatora CLSID obiektu.

::: moniker-end

## <a name="see-also"></a>Zobacz też

[Składnik ATL COM+ 1,0](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)
