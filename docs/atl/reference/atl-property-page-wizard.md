---
title: Kreator strony właściwości ATL
ms.date: 05/09/2019
f1_keywords:
- vc.codewiz.class.atl.ppg.overview
helpviewer_keywords:
- ATL projects, adding property pages
- ATL Property Page Wizard
ms.assetid: 6113e325-facd-4f68-b491-144d75209922
ms.openlocfilehash: eaf070d5a98a05dbe3102afac8317ffd59298ad2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321675"
---
# <a name="atl-property-page-wizard"></a>Kreator strony właściwości ATL

::: moniker range="vs-2019"

Ten kreator nie jest dostępny w programie Visual Studio 2019 i nowszych.

::: moniker-end

::: moniker range="<=vs-2017"

Ten kreator [dodaje stronę właściwości do projektu ATL](../../atl/reference/adding-an-atl-property-page.md) lub do projektu MFC z obsługą ATL. Strona właściwości ATL udostępnia interfejs użytkownika służący do ustawiania właściwości (lub wywoływania metod) jednego lub większej liczby obiektów COM.

## <a name="remarks"></a>Uwagi

Począwszy od programu Visual Studio 2008, skrypt rejestracji wyprodukowany przez tego kreatora zarejestruje swoje składniki COM w obszarze **HKEY_CURRENT_USER** zamiast **HKEY_LOCAL_MACHINE**. Aby zmodyfikować to zachowanie, należy ustawić **opcję Zarejestruj składnik dla wszystkich użytkowników** Kreatora ATL.

## <a name="names"></a>Nazwy

Określ nazwy obiektu, interfejsu i klas, które mają zostać dodane do projektu. Z wyjątkiem **krótkiej nazwy,** wszystkie inne pola mogą być edytowane niezależnie. Jeśli zmienisz tekst **dla krótkiej nazwy,** zmiana zostanie odzwierciedlona w nazwach wszystkich innych pól na tej stronie. Jeśli zmienisz nazwę **Coclass** w sekcji COM, zmiana zostanie odzwierciedlona w polach **Typ** i **ProgID.** To zachowanie nazewnictwa jest przeznaczony do wszystkich nazw łatwo rozpoznawalne dla Ciebie podczas tworzenia strony właściwości.

> [!NOTE]
> **Coclass** jest edytowalny tylko w projektach nieprzypisanych. Jeśli projekt jest przypisany, nie można edytować **programu Coclass**.

### <a name="c"></a>C++

Zawiera informacje dla klasy C++ utworzonej w celu zaimplementowania obiektu.

|||
|-|-|
|Termin|Definicja|
|**Krótka nazwa**|Ustawia skróconą nazwę obiektu. Podana nazwa określa nazwy klasy i **coclass,** nazwy plików (**.cpp** i **.h),** nazwę **typu** i **progid**, chyba że zmienisz te pola indywidualnie.|
|**.h plik**|Ustawia nazwę pliku nagłówka dla klasy nowego obiektu. Domyślnie ta nazwa jest oparta na nazwie podajona w **skróconej nazwie**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji lub dołączyć deklarację klasy do istniejącego pliku. Jeśli wybierzesz istniejący plik, kreator nie zapisze go w wybranej lokalizacji, dopóki nie klikniesz **przycisku Zakończ** w kreatorze.<br /><br /> Kreator nie zastępuje pliku. Jeśli wybierzesz nazwę istniejącego pliku, po kliknięciu **przycisku Zakończ**kreator wyświetli monit o wskazanie, czy deklaracja klasy powinna być dołączona do zawartości pliku. Kliknij **przycisk Tak,** aby dołączyć plik; Kliknij przycisk **Nie,** aby powrócić do kreatora i określić inną nazwę pliku.|
|**Klasa**|Ustawia nazwę klasy, która implementuje obiekt. Ta nazwa jest oparta na nazwie podającej w **skróconej nazwie,** poprzedzonej "C", typowym prefiksem nazwy klasy.|
|**.cpp**|Ustawia nazwę pliku implementacji dla klasy nowego obiektu. Domyślnie ta nazwa jest oparta na nazwie podajona w **skróconej nazwie**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji. Plik nie zostanie zapisany w wybranej lokalizacji, dopóki nie klikniesz **przycisku Zakończ** w kreatorze.<br /><br /> Kreator nie zastępuje pliku. Jeśli wybierzesz nazwę istniejącego pliku, po kliknięciu **przycisku Zakończ,** kreator wyświetli monit o wskazanie, czy implementacja klasy powinna być dołączona do zawartości pliku. Kliknij **przycisk Tak,** aby dołączyć plik; Kliknij przycisk **Nie,** aby powrócić do kreatora i określić inną nazwę pliku.|
|**Przypisane**|Wskazuje, czy obiekt używa atrybutów. Jeśli dodajesz obiekt do przypisanego projektu ATL, ta opcja jest zaznaczona i nie jest dostępna do zmiany, oznacza to, że można dodać tylko przypisane obiekty do projektu utworzonego za pomocą obsługi atrybutów.<br /><br /> Przypisany obiekt można dodać tylko do projektu ATL, który używa atrybutów. Jeśli wybierzesz tę opcję dla projektu ATL, który nie obsługuje atrybutów, kreator monituje o określenie, czy chcesz dodać obsługę atrybutów do projektu.<br /><br /> Domyślnie wszystkie obiekty dodane po ustawieniu tej opcji są oznaczone jako przypisane (zaznaczone jest pole wyboru). To pole można wyczyścić, aby dodać obiekt, który nie używa atrybutów.<br /><br /> Aby uzyskać więcej informacji, zobacz [Ustawienia aplikacji, Kreator projektu ATL](../../atl/reference/application-settings-atl-project-wizard.md) i [podstawowa mechanika atrybutów.](../../windows/basic-mechanics-of-attributes.md)|

### <a name="com"></a>Model COM

Zawiera informacje o funkcjach COM dla obiektu.

- **Coclass**

   Ustawia nazwę klasy składnika zawierającej listę interfejsów obsługiwanych przez obiekt.

   > [!NOTE]
   > Jeśli projekt zostanie utworzony przy użyciu atrybutów lub jeśli na tej stronie kreatora zostanie wszerz, `coclass` że strona właściwości używa atrybutów, nie można zmienić tej opcji, ponieważ atl nie zawiera atrybutu.

- **Typ**

   Ustawia opis obiektu, który pojawi się w rejestrze

- **Progid**

   Ustawia nazwę, której kontenery mogą używać zamiast identyfikatora CLSID obiektu.

::: moniker-end

## <a name="see-also"></a>Zobacz też

[Opcje, Kreator strony właściwości ATL](../../atl/reference/options-atl-property-page-wizard.md)<br/>
[Ciągi, Kreator strony właściwości ATL](../../atl/reference/strings-atl-property-page-wizard.md)<br/>
[Przykład: Implementowanie strony właściwości](../../atl/example-implementing-a-property-page.md)
