---
title: Kreator składników ATL COM+ 1.0
ms.date: 05/08/2019
helpviewer_keywords:
- ATL projects, adding components
ms.assetid: 11670681-8671-4122-96a4-2e52f8dadce0
ms.openlocfilehash: d5c0c0c8edb6b698d3d8f50736121d987af98492
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321690"
---
# <a name="atl-com-10-component-wizard"></a>Kreator składników ATL COM+ 1.0

::: moniker range="vs-2019"

Ten kreator nie jest dostępny w programie Visual Studio 2019 i nowszych.

::: moniker-end

::: moniker range="<=vs-2017"

Ten kreator służy do dodawania obiektu do projektu, który obsługuje usługi COM+ 1.0, w tym transakcje.

Można określić, czy obiekt obsługuje dwa interfejsy i automatyzacji. Można również wskazać obsługę interfejsu informacji o błędzie, ulepszonej kontroli obiektu, transakcji i kolejkowania komunikatów asynchronicznych.

## <a name="remarks"></a>Uwagi

Począwszy od programu Visual Studio 2008, skrypt rejestracji wyprodukowany przez tego kreatora zarejestruje swoje składniki COM w obszarze **HKEY_CURRENT_USER** zamiast **HKEY_LOCAL_MACHINE**. Aby zmodyfikować to zachowanie, należy ustawić **opcję Zarejestruj składnik dla wszystkich użytkowników** Kreatora ATL.

## <a name="names"></a>Nazwy

Określ nazwy obiektu, interfejsu i klas, które mają zostać dodane do projektu. Z wyjątkiem **krótkiej nazwy,** wszystkie inne pola mogą być edytowane niezależnie od innych. Jeśli zmienisz tekst **dla krótkiej nazwy,** zmiana zostanie odzwierciedlona w nazwach wszystkich innych pól na tej stronie. Jeśli zmienisz nazwę **Coclass** w sekcji COM, zmiana zostanie odzwierciedlona w polach **Typ** i **ProgID,** ale nazwa **interfejsu** nie ulegnie zmianie. To zachowanie nazewnictwa jest przeznaczony do wszystkich nazw łatwo rozpoznawalne dla Ciebie podczas rozwijania kontroli.

- **Krótka nazwa**

   Ustawia skróconą nazwę obiektu. Podana nazwa określa `Class` nazwy `Coclass` i nazwy, **nazwy plików cpp** i **.h,** nazwę **interfejsu,** nazwy **typów** i **identyfikator progid**, chyba że pola te zostaną zmienić indywidualnie.

- **.h plik**

   Ustawia nazwę pliku nagłówka dla klasy nowego obiektu. Domyślnie ta nazwa jest oparta na nazwie podajona w **skróconej nazwie**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji lub dołączyć deklarację klasy do istniejącego pliku. Jeśli wybierzesz istniejący plik, kreator nie zapisze go w wybranej lokalizacji, dopóki nie klikniesz **przycisku Zakończ** w kreatorze.

   Kreator nie zastępuje pliku. Jeśli wybierzesz nazwę istniejącego pliku, po kliknięciu **przycisku Zakończ**kreator wyświetli monit o wskazanie, czy deklaracja klasy powinna być dołączona do zawartości pliku. Kliknij **przycisk Tak,** aby dołączyć plik; Kliknij przycisk **Nie,** aby powrócić do kreatora i określić inną nazwę pliku.

- **Klasa**

   Ustawia nazwę klasy, która ma zostać utworzona. Ta nazwa jest oparta na nazwie podającej w **skróconej nazwie,** poprzedzonej "C", typowym prefiksem nazwy klasy.

- **.cpp**

   Ustawia nazwę pliku implementacji dla klasy nowego obiektu. Domyślnie ta nazwa jest oparta na nazwie podajona w **skróconej nazwie**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji. Plik nie zostanie zapisany w wybranej lokalizacji, dopóki nie klikniesz **przycisku Zakończ** w kreatorze.

   Kreator nie zastępuje pliku. Jeśli wybierzesz nazwę istniejącego pliku, po kliknięciu **przycisku Zakończ,** kreator wyświetli monit o wskazanie, czy implementacja klasy powinna być dołączona do zawartości pliku. Kliknij **przycisk Tak,** aby dołączyć plik; Kliknij przycisk **Nie,** aby powrócić do kreatora i określić inną nazwę pliku.

- **Przypisane**

   Wskazuje, czy obiekt używa atrybutów. Jeśli dodajesz obiekt do przypisanego projektu ATL, ta opcja jest zaznaczona i nie jest dostępna do zmiany. Oznacza to, że można dodać tylko przypisane obiekty do projektu utworzonego za pomocą obsługi atrybutów.

   Jeśli wybierzesz tę opcję dla projektu ATL, który nie obsługuje atrybutów, kreator monituje o określenie, czy chcesz dodać obsługę atrybutów do projektu.

   Wszystkie obiekty dodane po tym ustawieniu ta opcja są domyślnie oznaczone jako przypisane (pole wyboru jest zaznaczone). To pole można wyczyścić, aby dodać obiekt, który nie używa atrybutów.

   Aby uzyskać więcej informacji, zobacz [Ustawienia aplikacji, Kreator projektu ATL](../../atl/reference/application-settings-atl-project-wizard.md) i [podstawowa mechanika atrybutów.](../../windows/basic-mechanics-of-attributes.md)

### <a name="com"></a>Model COM

Zawiera informacje o funkcjach COM dla obiektu.

- **Coclass**

   Ustawia nazwę klasy składnika zawierającej listę interfejsów obsługiwanych przez obiekt.

> [!NOTE]
> Jeśli projekt zostanie utworzony przy użyciu atrybutów lub na tej stronie kreatora wskażesz, że składnik COM+ 1.0 używa atrybutów, nie można zmienić tej opcji, ponieważ atl nie zawiera atrybutu. `coclass`

- **Typ**

   Ustawia opis obiektu, który pojawi się w rejestrze

- **Interfejs**

   Ustawia interfejs utworzony dla obiektu. Ten interfejs zawiera metody niestandardowe.

- **Progid**

   Ustawia nazwę, której kontenery mogą używać zamiast identyfikatora CLSID obiektu.

::: moniker-end

## <a name="see-also"></a>Zobacz też

[Komponent ATL COM+ 1.0](../../atl/reference/adding-an-atl-com-plus-1-0-component.md)
