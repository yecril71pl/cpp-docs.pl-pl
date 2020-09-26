---
title: Kreator strony właściwości ATL
ms.date: 05/09/2019
f1_keywords:
- vc.codewiz.class.atl.ppg.overview
helpviewer_keywords:
- ATL projects, adding property pages
- ATL Property Page Wizard
ms.assetid: 6113e325-facd-4f68-b491-144d75209922
ms.openlocfilehash: c25e3b9194cf0c7dc7c152edb50be01def2d2d9b
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352730"
---
# <a name="atl-property-page-wizard"></a>Kreator strony właściwości ATL

::: moniker range="vs-2019"

Ten Kreator nie jest dostępny w programie Visual Studio 2019 i nowszych.

::: moniker-end

::: moniker range="<=vs-2017"

Ten Kreator [dodaje stronę właściwości do projektu ATL](../../atl/reference/adding-an-atl-property-page.md) lub do projektu MFC z obsługą ATL. Strona właściwości ATL udostępnia interfejs użytkownika służący do ustawiania właściwości (lub wywoływania metod) jednego lub większej liczby obiektów COM.

## <a name="remarks"></a>Uwagi

Począwszy od programu Visual Studio 2008 skrypt rejestracji utworzony przez tego kreatora spowoduje zarejestrowanie jego składników modelu COM w **HKEY_CURRENT_USER** , a nie **HKEY_LOCAL_MACHINE**. Aby zmienić to zachowanie, ustaw opcję **Zarejestruj składnik dla wszystkich użytkowników** w Kreatorze ATL.

## <a name="names"></a>Nazwy

Określ nazwy obiektu, interfejsu i klas, które mają zostać dodane do projektu. Oprócz **krótkiej nazwy**wszystkie inne pola można edytować niezależnie. Jeśli zmienisz tekst **skróconej nazwy**, zmiana zostanie odzwierciedlona w nazwach wszystkich innych pól na tej stronie. Jeśli zmienisz nazwę **klasy coclass** w sekcji com, zmiana zostanie odzwierciedlona w polach **Typ** i **ProgID** . To zachowanie nazewnictwa zostało zaprojektowane tak, aby wszystkie nazwy były łatwo rozpoznawalne podczas tworzenia strony właściwości.

> [!NOTE]
> **Klasy coclass** można edytować tylko w projektach niebędących atrybutami. Jeśli projekt nie jest przypisany, nie można edytować **klasy coclass**.

### <a name="c"></a>C++

Zawiera informacje dotyczące klasy języka C++, która została utworzona w celu zaimplementowania obiektu.

|Termin|Definicja|
|-|-|
|**Krótka nazwa**|Ustawia skróconą nazwę obiektu. Nazwa dostarczana przez użytkownika określa **klasy i nazwy klas,** nazwy plików (**. cpp** i **. h**), nazwę **typu** i **Identyfikator ProgID**, chyba że te pola są zmieniane pojedynczo.|
|**plik h**|Ustawia nazwę pliku nagłówka dla klasy nowego obiektu. Domyślnie ta nazwa jest oparta na nazwie podanym w polu **krótka nazwa**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji, lub dołączyć deklarację klasy do istniejącego pliku. W przypadku wybrania istniejącego pliku Kreator nie zapisze go w wybranej lokalizacji, dopóki nie zostanie kliknięty przycisk **Zakończ** w kreatorze.<br /><br /> Kreator nie zastępuje pliku. Jeśli wybierzesz nazwę istniejącego pliku, po kliknięciu przycisku **Zakończ**Kreator monituje o wskazanie, czy deklaracja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** , aby dołączyć plik; Kliknij przycisk **nie** , aby powrócić do kreatora i określić inną nazwę pliku.|
|**Klasa**|Ustawia nazwę klasy implementującej obiekt. Ta nazwa jest oparta na nazwie, którą podano w **krótkiej nazwie**, poprzedzonej znakiem "C", typowym prefiksem dla nazwy klasy.|
|**plik. cpp**|Ustawia nazwę pliku implementacji dla klasy nowego obiektu. Domyślnie ta nazwa jest oparta na nazwie podanym w polu **krótka nazwa**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji. Plik nie jest zapisywany w wybranej lokalizacji, dopóki nie zostanie kliknięty przycisk **Zakończ** w kreatorze.<br /><br /> Kreator nie zastępuje pliku. W przypadku wybrania nazwy istniejącego pliku po kliknięciu przycisku **Zakończ**Kreator monituje o wskazanie, czy implementacja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** , aby dołączyć plik; Kliknij przycisk **nie** , aby powrócić do kreatora i określić inną nazwę pliku.|
|**Przypisanych**|Wskazuje, czy obiekt używa atrybutów. Jeśli dodajesz obiekt do projektu ATL z atrybutami, ta opcja jest zaznaczona i nie jest dostępna do zmiany, oznacza to, że można dodawać tylko obiekty z atrybutami do projektu utworzonego z obsługą atrybutu.<br /><br /> Obiekt atrybutu można dodać tylko do projektu ATL, który używa atrybutów. W przypadku wybrania tej opcji dla projektu ATL, który nie obsługuje atrybutu, Kreator poprosi o określenie, czy chcesz dodać obsługę atrybutu do projektu.<br /><br /> Domyślnie wszystkie obiekty dodane po ustawieniu tej opcji są oznaczone jako przypisane do atrybutu (pole wyboru jest zaznaczone). Możesz wyczyścić to pole, aby dodać obiekt, który nie używa atrybutów.<br /><br /> Aby uzyskać więcej informacji [, zobacz Ustawienia aplikacji, Kreator projektu ATL](../../atl/reference/application-settings-atl-project-wizard.md) i [podstawowe Mechanics atrybutów](../../windows/attributes/cpp-attributes-com-net.md#basic-mechanics-of-attributes) .|

### <a name="com"></a>Model COM

Zawiera informacje o funkcji COM dla obiektu.

- **Klasa coclass**

   Ustawia nazwę klasy składnika, która zawiera listę interfejsów obsługiwanych przez obiekt.

   > [!NOTE]
   > Jeśli tworzysz projekt przy użyciu atrybutów lub w przypadku wybrania tej strony kreatora, że strona właściwości używa atrybutów, nie można zmienić tej opcji, ponieważ ATL nie zawiera `coclass` atrybutu.

- **Typ**

   Ustawia opis obiektu, który będzie wyświetlany w rejestrze

- **ProgID**

   Ustawia nazwę, która może być używana przez kontenery zamiast identyfikatora CLSID obiektu.

::: moniker-end

## <a name="see-also"></a>Zobacz też

[Opcje, Kreator strony właściwości ATL](../../atl/reference/options-atl-property-page-wizard.md)<br/>
[Ciągi, Kreator strony właściwości ATL](../../atl/reference/strings-atl-property-page-wizard.md)<br/>
[Przykład: implementowanie strony właściwości](../../atl/example-implementing-a-property-page.md)
