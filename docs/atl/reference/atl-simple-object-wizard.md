---
title: Kreator prostych obiektów ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.simple.overview
helpviewer_keywords:
- ATL projects, adding objects
- ATL Simple Object Wizard
ms.assetid: f7f85741-9aad-4543-a917-a29b996364da
ms.openlocfilehash: 8bc611442e98e467a174ebd52ea3c540cf72975f
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352690"
---
# <a name="atl-simple-object-wizard"></a>Kreator prostych obiektów ATL

Ten Kreator wstawia do projektu minimalny obiekt COM. Ta strona kreatora służy do określania nazw, które identyfikują klasę i pliki języka C++ dla obiektu i jego funkcji COM.

Za pomocą strony [Opcje](../../atl/reference/options-atl-simple-object-wizard.md) tego kreatora można określić model wątkowości obiektu, jego obsługę agregacji oraz czy obsługuje ona dwa interfejsy i automatyzację. Możesz również wskazać obsługę interfejsu informacji o błędach, punktów połączenia, pomocy technicznej programu Internet Explorer i organizowania wolnych wątków.

## <a name="remarks"></a>Uwagi

Począwszy od programu Visual Studio 2008 skrypt rejestracji utworzony przez tego kreatora spowoduje zarejestrowanie jego składników modelu COM w **HKEY_CURRENT_USER** , a nie **HKEY_LOCAL_MACHINE**. Aby zmienić to zachowanie, ustaw opcję **Zarejestruj składnik dla wszystkich użytkowników** w Kreatorze ATL.

## <a name="names"></a>Nazwy

Określ nazwy obiektu, interfejsu i klas, które mają zostać dodane do projektu. Oprócz **krótkiej nazwy**wszystkie inne pola można edytować niezależnie od innych. Jeśli zmienisz tekst **skróconej nazwy**, zmiana zostanie odzwierciedlona w nazwach wszystkich innych pól na tej stronie. Jeśli zmienisz nazwę **klasy coclass** w sekcji com, zmiana zostanie odzwierciedlona w polach **Typ** i **ProgID** , ale nazwa **interfejsu** nie zostanie zmieniona. Takie zachowanie nazewnictwa zostało zaprojektowane, aby wszystkie nazwy były łatwo rozpoznawalne podczas tworzenia kontrolki.

> [!NOTE]
> **Klasy coclass** można edytować tylko w projektach niebędących atrybutami. Jeśli projekt nie jest przypisany, nie można edytować **klasy coclass**.

## <a name="c"></a>C++

Zawiera informacje o klasie C++ utworzonej dla obiektu.

- **Krótka nazwa**

   Ustawia skróconą nazwę obiektu. Nazwa dostarczana przez użytkownika określa nazwy `Class` i nazwy `Coclass` plików **. cpp** oraz **. h** , nazwę **interfejsu** , nazwy **typów** i **Identyfikator ProgID**, chyba że te pola są zmieniane pojedynczo.

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

   Obiekt atrybutu można dodać tylko do projektu ATL, który używa atrybutów. W przypadku wybrania tej opcji dla projektu ATL, który nie obsługuje atrybutu, Kreator poprosi o określenie, czy chcesz dodać obsługę atrybutu do projektu.

   Domyślnie wszystkie obiekty dodane po ustawieniu tej opcji są oznaczone jako przypisane do atrybutu (pole wyboru jest zaznaczone). Możesz wyczyścić to pole, aby dodać obiekt, który nie używa atrybutów.

   Aby uzyskać więcej informacji [, zobacz Ustawienia aplikacji, Kreator projektu ATL](../../atl/reference/application-settings-atl-project-wizard.md) i [podstawowe Mechanics atrybutów](../../windows/attributes/cpp-attributes-com-net.md#basic-mechanics-of-attributes) .

## <a name="com"></a>Model COM

Zawiera informacje o funkcji COM dla obiektu.

- **Klasa coclass**

   Ustawia nazwę klasy składnika, która zawiera listę interfejsów obsługiwanych przez obiekt.

   > [!NOTE]
   > Jeśli tworzysz projekt przy użyciu atrybutów lub wskażesz Tę stronę kreatora, że obiekt używa atrybutów, nie można zmienić tej opcji, ponieważ ATL nie zawiera `coclass` atrybutu.

- **Typ**

   Ustawia opis obiektu, który będzie wyświetlany w rejestrze

- **Interfejs**

   Ustawia interfejs tworzony dla obiektu. Ten interfejs zawiera własne metody.

- **ProgID**

   Ustawia nazwę, która może być używana przez kontenery zamiast identyfikatora CLSID obiektu.

## <a name="see-also"></a>Zobacz też

[Prosty obiekt ATL](../../atl/reference/adding-an-atl-simple-object.md)
