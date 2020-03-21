---
title: Kreator składników ATL COM+ 1.0
ms.date: 05/08/2019
helpviewer_keywords:
- ATL projects, adding components
ms.assetid: 11670681-8671-4122-96a4-2e52f8dadce0
ms.openlocfilehash: eaecd0d4e6e2b024ce3312719e7104298d3f9a66
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075283"
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

   Ustawia skróconą nazwę obiektu. Podane przez użytkownika nazwy określają nazwy `Class` i `Coclass`, **plik. cpp** i nazwy plików. **h** , nazwę **interfejsu** , nazwy **typów** i **ProgID**, chyba że te pola są zmieniane pojedynczo.

- **plik h**

   Ustawia nazwę pliku nagłówka dla klasy nowego obiektu. Domyślnie ta nazwa jest oparta na nazwie podanym w polu **krótka nazwa**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji, lub dołączyć deklarację klasy do istniejącego pliku. Jeśli wybierzesz istniejący plik, Kreator nie zapisze go w wybranej lokalizacji, dopóki nie klikniesz przycisku **Zakończ** w kreatorze.

   Kreator nie zastępuje pliku. Jeśli wybierzesz nazwę istniejącego pliku, po kliknięciu przycisku **Zakończ**Kreator monituje o wskazanie, czy deklaracja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** , aby dołączyć plik; Kliknij przycisk **nie** , aby powrócić do kreatora i określić inną nazwę pliku.

- **Określonej**

   Ustawia nazwę klasy, która ma zostać utworzona. Ta nazwa jest oparta na nazwie podanym w **skrócie nazwa**, poprzedzona znakiem "C", typowym prefiksem dla nazwy klasy.

- **plik. cpp**

   Ustawia nazwę pliku implementacji dla klasy nowego obiektu. Domyślnie ta nazwa jest oparta na nazwie podanym w polu **krótka nazwa**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji. Plik nie jest zapisywany w wybranej lokalizacji, dopóki nie zostanie kliknięty przycisk **Zakończ** w kreatorze.

   Kreator nie zastępuje pliku. W przypadku wybrania nazwy istniejącego pliku po kliknięciu przycisku **Zakończ**Kreator monituje o wskazanie, czy implementacja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** , aby dołączyć plik; Kliknij przycisk **nie** , aby powrócić do kreatora i określić inną nazwę pliku.

- **Przypisanych**

   Wskazuje, czy obiekt używa atrybutów. Jeśli dodajesz obiekt do projektu ATL z atrybutami, ta opcja jest zaznaczona i nie można jej zmienić. Oznacza to, że można dodawać tylko obiekty z atrybutami do projektu utworzonego za pomocą obsługi atrybutu.

   W przypadku wybrania tej opcji dla projektu ATL, który nie obsługuje atrybutu, Kreator poprosi o określenie, czy chcesz dodać obsługę atrybutu do projektu.

   Wszystkie obiekty dodane po ustawieniu tej opcji są oznaczone domyślnie jako przypisane do atrybutu (pole wyboru jest zaznaczone). Możesz wyczyścić to pole, aby dodać obiekt, który nie używa atrybutów.

   Aby uzyskać więcej informacji [, zobacz Ustawienia aplikacji, Kreator projektu ATL](../../atl/reference/application-settings-atl-project-wizard.md) i [podstawowe Mechanics atrybutów](../../windows/basic-mechanics-of-attributes.md) .

### <a name="com"></a>Model COM

Zawiera informacje o funkcji COM dla obiektu.

- **Klasa coclass**

   Ustawia nazwę klasy składnika, która zawiera listę interfejsów obsługiwanych przez obiekt.

> [!NOTE]
>  Jeśli tworzysz projekt przy użyciu atrybutów lub w przypadku wybrania na tej stronie kreatora, że składnik COM+ 1,0 używa atrybutów, nie można zmienić tej opcji, ponieważ ATL nie zawiera atrybutu `coclass`.

- **Typ**

   Ustawia opis obiektu, który będzie wyświetlany w rejestrze

- **Interfejsu**

   Ustawia interfejs tworzony dla obiektu. Ten interfejs zawiera własne metody.

- **ProgID**

   Ustawia nazwę, która może być używana przez kontenery zamiast identyfikatora CLSID obiektu.

::: moniker-end

## <a name="see-also"></a>Zobacz też

[Składnik ATL COM+ 1,0](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)
