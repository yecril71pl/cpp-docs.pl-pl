---
title: Kreator prostych obiektów ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.simple.overview
helpviewer_keywords:
- ATL projects, adding objects
- ATL Simple Object Wizard
ms.assetid: f7f85741-9aad-4543-a917-a29b996364da
ms.openlocfilehash: bd4c9eede16ed086020dd8f12d90876e50a0a341
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319202"
---
# <a name="atl-simple-object-wizard"></a>Kreator prostych obiektów ATL

Ten kreator wstawia do projektu minimalny obiekt COM. Ta strona kreatora służy do określania nazw identyfikujących klasę C++ i pliki dla obiektu i jego funkcji COM.

Użyj [opcji](../../atl/reference/options-atl-simple-object-wizard.md) strony tego kreatora, aby określić model wątków obiektu, jego obsługi agregacji i czy obsługuje dwa interfejsy i automatyzacji. Można również wskazać obsługę interfejsu informacji o błędzie, punktów połączenia, obsługi programu Internet Explorer i organizowania bezwątpowego.

## <a name="remarks"></a>Uwagi

Począwszy od programu Visual Studio 2008, skrypt rejestracji wyprodukowany przez tego kreatora zarejestruje swoje składniki COM w obszarze **HKEY_CURRENT_USER** zamiast **HKEY_LOCAL_MACHINE**. Aby zmodyfikować to zachowanie, należy ustawić **opcję Zarejestruj składnik dla wszystkich użytkowników** Kreatora ATL.

## <a name="names"></a>Nazwy

Określ nazwy obiektu, interfejsu i klas, które mają zostać dodane do projektu. Z wyjątkiem **krótkiej nazwy,** wszystkie inne pola mogą być edytowane niezależnie od innych. Jeśli zmienisz tekst **dla krótkiej nazwy,** zmiana zostanie odzwierciedlona w nazwach wszystkich innych pól na tej stronie. Jeśli zmienisz nazwę **Coclass** w sekcji COM, zmiana zostanie odzwierciedlona w polach **Typ** i **ProgID,** ale nazwa **interfejsu** nie ulegnie zmianie. To zachowanie nazewnictwa jest przeznaczony do wszystkich nazw łatwo rozpoznawalne dla Ciebie podczas rozwijania kontroli.

> [!NOTE]
> **Coclass** jest edytowalny tylko w projektach nieprzypisanych. Jeśli projekt jest przypisany, nie można edytować **programu Coclass**.

## <a name="c"></a>C++

Zawiera informacje dla klasy C++ utworzonej dla obiektu.

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

   Przypisany obiekt można dodać tylko do projektu ATL, który używa atrybutów. Jeśli wybierzesz tę opcję dla projektu ATL, który nie obsługuje atrybutów, kreator monituje o określenie, czy chcesz dodać obsługę atrybutów do projektu.

   Domyślnie wszystkie obiekty dodane po ustawieniu tej opcji są oznaczone jako przypisane (zaznaczone jest pole wyboru). To pole można wyczyścić, aby dodać obiekt, który nie używa atrybutów.

   Aby uzyskać więcej informacji, zobacz [Ustawienia aplikacji, Kreator projektu ATL](../../atl/reference/application-settings-atl-project-wizard.md) i [podstawowa mechanika atrybutów.](../../windows/basic-mechanics-of-attributes.md)

## <a name="com"></a>Model COM

Zawiera informacje o funkcjach COM dla obiektu.

- **Coclass**

   Ustawia nazwę klasy składnika zawierającej listę interfejsów obsługiwanych przez obiekt.

   > [!NOTE]
   > Jeśli projekt zostanie utworzony przy użyciu atrybutów lub jeśli na tej stronie kreatora zostanie wskazane, że `coclass` obiekt używa atrybutów, nie można zmienić tej opcji, ponieważ atl nie zawiera atrybutu.

- **Typ**

   Ustawia opis obiektu, który pojawi się w rejestrze

- **Interfejs**

   Ustawia interfejs utworzony dla obiektu. Ten interfejs zawiera metody niestandardowe.

- **Progid**

   Ustawia nazwę, której kontenery mogą używać zamiast identyfikatora CLSID obiektu.

## <a name="see-also"></a>Zobacz też

[Prosty obiekt ATL](../../atl/reference/adding-an-atl-simple-object.md)
