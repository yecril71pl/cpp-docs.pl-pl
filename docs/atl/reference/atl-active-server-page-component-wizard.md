---
title: Kreator składników stron Active Server Page ATL
ms.date: 05/09/2019
helpviewer_keywords:
- ASP components, creating in ATL
ms.assetid: 5a5cb904-dbbf-44ea-ad3d-2ddd14c1d3c5
ms.openlocfilehash: 3e29d049c50f0410daf16b4bd1322676fd499fd2
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352677"
---
# <a name="atl-active-server-page-component-wizard"></a>Kreator składników stron Active Server Page ATL

::: moniker range="vs-2019"

Ten Kreator nie jest dostępny w programie Visual Studio 2019 i nowszych.

::: moniker-end

::: moniker range="<=vs-2017"

Ten Kreator wstawia do projektu składnik strony Active Server (ASP). Program Microsoft Internet Information Services (IIS) używa składników ASP jako części ulepszonej architektury tworzenia stron sieci Web.

Za pomocą tego kreatora można określić model wątkowości składnika i jego obsługę agregacji. Możesz również wskazać pomoc techniczną dla interfejsu informacji o błędach, punktów połączenia i organizowania w dowolnym wątku.

## <a name="remarks"></a>Uwagi

Począwszy od programu Visual Studio 2008 skrypt rejestracji utworzony przez tego kreatora rejestruje jego składniki COM w **HKEY_CURRENT_USER** , a nie **HKEY_LOCAL_MACHINE**. Aby zmienić to zachowanie, ustaw opcję **Zarejestruj składnik dla wszystkich użytkowników** w Kreatorze ATL.

## <a name="names"></a>Nazwy

Określ nazwy obiektu, interfejsu i klas, które mają zostać dodane do projektu. Oprócz **krótkiej nazwy**wszystkie inne pola można edytować niezależnie od innych. Jeśli zmienisz tekst **skróconej nazwy**, zmiana zostanie odzwierciedlona w nazwach wszystkich innych pól na tej stronie.

Jeśli zmienisz nazwę **klasy coclass** w sekcji com, zmiana zostanie odzwierciedlona w polach **Typ** i **ProgID** , ale nazwa **interfejsu** nie zostanie zmieniona. Takie zachowanie nazewnictwa zostało zaprojektowane, aby wszystkie nazwy były łatwo rozpoznawalne podczas tworzenia kontrolki.

### <a name="c"></a>C++

Zawiera informacje o klasie C++ utworzonej dla obiektu.

- **Krótka nazwa**

   Ustawia nazwę główną dla obiektu. Nazwa dostarczana przez użytkownika określa `Class` nazwy i **klasy coclass** , **plik. cpp** i nazwy **plików. h** , nazwę **interfejsu** , nazwy **typów** i **Identyfikator ProgID**, chyba że te pola są zmieniane pojedynczo.

- **plik h**

   Ustawia nazwę pliku nagłówka dla klasy nowego obiektu. Domyślnie ta nazwa jest oparta na nazwie podanym w polu **krótka nazwa**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji, lub dołączyć deklarację klasy do istniejącego pliku. W przypadku wybrania istniejącego pliku Kreator nie zapisze go w wybranej lokalizacji, dopóki nie zostanie kliknięty przycisk **Zakończ** w kreatorze.

   Kreator nie zastępuje pliku. Jeśli wybierzesz nazwę istniejącego pliku, po kliknięciu przycisku **Zakończ**Kreator monituje o wskazanie, czy deklaracja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** , aby dołączyć plik; Kliknij przycisk **nie** , aby powrócić do kreatora i określić inną nazwę pliku.

- **Klasa**

   Ustawia nazwę klasy, która ma zostać utworzona. Ta nazwa jest oparta na nazwie, którą podano w **krótkiej nazwie**, poprzedzonej znakiem "C", typowym prefiksem dla nazwy klasy.

- **plik. cpp**

   Ustawia nazwę pliku implementacji dla klasy nowego obiektu. Domyślnie ta nazwa jest oparta na nazwie podanym w polu **krótka nazwa**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji. Plik nie jest zapisywany w wybranej lokalizacji, dopóki nie zostanie kliknięty przycisk **Zakończ** w kreatorze.

   Kreator nie zastępuje pliku. W przypadku wybrania nazwy istniejącego pliku po kliknięciu przycisku **Zakończ**Kreator monituje o wskazanie, czy implementacja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** , aby dołączyć plik; Kliknij przycisk **nie** , aby powrócić do kreatora i określić inną nazwę pliku.

- **Przypisanych**

   Wskazuje, czy obiekt używa atrybutów. Jeśli dodajesz obiekt do projektu ATL z atrybutami, ta opcja jest zaznaczona i nie można jej zmienić. Oznacza to, że można dodawać tylko obiekty z atrybutami do projektu utworzonego za pomocą obsługi atrybutu.

   W przypadku wybrania tej opcji dla projektu ATL, który nie obsługuje atrybutu, Kreator poprosi o określenie, czy chcesz dodać obsługę atrybutu do projektu.

   Domyślnie dla projektów nienależących do atrybutu, wszystkie obiekty dodane po ustawieniu tej opcji są oznaczone jako przypisane do atrybutu (pole wyboru jest zaznaczone). Możesz wyczyścić to pole, aby dodać obiekt, który nie używa atrybutów.

   Aby uzyskać więcej informacji [, zobacz Ustawienia aplikacji, Kreator projektu ATL](../../atl/reference/application-settings-atl-project-wizard.md) i [podstawowe Mechanics atrybutów](../../windows/attributes/cpp-attributes-com-net.md#basic-mechanics-of-attributes) .

### <a name="com"></a>Model COM

Zawiera informacje o funkcji COM dla obiektu.

- **Klasa coclass**

   Ustawia nazwę klasy składnika, która zawiera listę interfejsów obsługiwanych przez obiekt. Jeśli projekt lub ten obiekt używa atrybutów, nie można zmienić tej opcji, ponieważ ATL nie zawiera atrybutu **coclass** .

- **Typ**

   Ustawia opis obiektu, który będzie wyświetlany w rejestrze dla klasy coclass.

- **Interfejs**

   Ustawia interfejs tworzony dla obiektu. Ten interfejs zawiera własne metody.

- **ProgID**

   Ustawia nazwę, która może być używana przez kontenery zamiast identyfikatora CLSID obiektu.

::: moniker-end

## <a name="see-also"></a>Zobacz też

[Składnik strony Active Server ATL](../../atl/reference/adding-an-atl-active-server-page-component.md)
