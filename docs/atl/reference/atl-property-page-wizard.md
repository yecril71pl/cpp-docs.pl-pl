---
title: Kreator strony właściwości ATL
ms.date: 05/09/2019
f1_keywords:
- vc.codewiz.class.atl.ppg.overview
helpviewer_keywords:
- ATL projects, adding property pages
- ATL Property Page Wizard
ms.assetid: 6113e325-facd-4f68-b491-144d75209922
ms.openlocfilehash: 47fee2291d201fca04674b07926ed88aaed0a95c
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2019
ms.locfileid: "65524531"
---
# <a name="atl-property-page-wizard"></a>Kreator strony właściwości ATL

::: moniker range="vs-2019"

Ten kreator nie jest dostępne w programie Visual Studio 2019 r i nowszych wersjach.

::: moniker-end

::: moniker range="vs-2017"

Ten kreator [dodaje strony właściwości w projekcie ATL](../../atl/reference/adding-an-atl-property-page.md) lub do projektu MFC z obsługą ATL. Strony właściwości ATL udostępnia interfejs użytkownika do ustawiania właściwości (lub wywoływania metod) jeden lub więcej obiektów COM.

## <a name="remarks"></a>Uwagi

Począwszy od programu Visual Studio 2008, skrypt rejestrowania generowane przez kreatora, będą rejestrować jego składników modelu COM, w obszarze **HKEY_CURRENT_USER** zamiast **HKEY_LOCAL_MACHINE**. Aby zmienić to zachowanie, ustaw **części rejestru dla wszystkich użytkowników** opcji kreatora ATL.

## <a name="names"></a>Nazwy

Określ nazwy dla obiektu, interfejsów i klas, które mają zostać dodane do projektu. Z wyjątkiem **krótką nazwę**, wszystkie inne pola, które mogą być edytowane niezależnie. Jeśli zmienisz tekst **krótką nazwę**, zmiany są widoczne w nazwach wszystkie inne pola na tej stronie. Jeśli zmienisz **Coclass** nazwę w sekcji COM, zmiana jest odzwierciedlana w **typu** i **ProgID** pola. To zachowanie nazewnictwa zaprojektowaną do podejmowania wszystkich nazw można łatwo zidentyfikować dla Ciebie podczas opracowywania stronę właściwości.

> [!NOTE]
>  **Klasa coclass** można edytować tylko nonattributed projektów. Jeśli projekt jest przypisane, nie można edytować **Coclass**.

### <a name="c"></a>C++

Zawiera informacje dla klasy języka C++ utworzona w celu wdrożenia obiektu.

|||
|-|-|
|Termin|Definicja|
|**Krótka nazwa**|Ustawia skróconą nazwę dla obiektu. Należy podać nazwę określa klasę i **Coclass** nazywa plik (**.cpp** i **.h**) nazw, **typu** nazwę i  **Identyfikator progID**, chyba że zmienił się tych pól indywidualnie.|
|**plik .h**|Określa nazwę pliku nagłówkowego klasy nowego obiektu. Domyślnie ta nazwa opiera się na nazwę, która zapewnia w **krótką nazwę**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku na lokalizację lub dołączyć deklaracji klasy do istniejącego pliku. Jeśli wybierzesz istniejący plik, Kreator nie zapisze go w wybranej lokalizacji do momentu kliknij **Zakończ** w kreatorze.<br /><br /> Kreator nie powoduje zastąpienia pliku. Jeśli wybierasz nazwę istniejącego pliku, po kliknięciu **Zakończ**, Kreator wyświetli monit o wskazują, czy deklaracja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** można dołączyć pliku kliknij przycisk **nie** aby powrócić do kreatora i podaj inną nazwę pliku.|
|**Class**|Ustawia nazwę klasy, która implementuje obiektu. Ta nazwa jest oparta na nazwę, która zapewnia w **krótką nazwę**, poprzedzającą "C", typowy prefiks dla nazwy klasy.|
|**Plik CPP**|Określa nazwę pliku implementacji dla nowego obiektu klasy. Domyślnie ta nazwa opiera się na nazwę, która zapewnia w **krótką nazwę**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji. Plik nie jest zapisywany w wybranej lokalizacji, dopóki nie klikniesz **Zakończ** w kreatorze.<br /><br /> Kreator nie powoduje zastąpienia pliku. Jeśli wybierasz nazwę istniejącego pliku, po kliknięciu **Zakończ**, Kreator wyświetli monit o wskazują, czy Implementacja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** można dołączyć pliku kliknij przycisk **nie** aby powrócić do kreatora i podaj inną nazwę pliku.|
|**Opartego na atrybutach**|Wskazuje, czy obiekt używa atrybutów. Jeśli dodajesz obiektu do projekcie ATL z atrybutami, ta opcja jest zaznaczona i nie można zmienić, oznacza to, że można dodawać tylko przypisane obiekty do projektu utworzonego za pomocą atrybutu pomocy technicznej.<br /><br /> Obiekt opartego na atrybutach można dodać tylko do projektu ATL, który używa atrybutów. Jeśli wybierzesz tę opcję, aby Projekt ATL, który nie ma atrybutu pomocy technicznej, w kreatora zostanie wyświetlony monit o określenie, czy chcesz dodać obsługę atrybutu do projektu.<br /><br /> Domyślnie wszystkie obiekty, które możesz dodać po ustawieniu tej opcji są oznaczone jako opartego na atrybutach (pole wyboru jest zaznaczone). Aby wyczyścić to pole, aby dodać obiekt, który nie korzysta z atrybutów.<br /><br /> Zobacz [ustawienia aplikacji, Kreator projektów ATL](../../atl/reference/application-settings-atl-project-wizard.md) i [podstawowa mechanika atrybutów](../../windows/basic-mechanics-of-attributes.md) Aby uzyskać więcej informacji.|

### <a name="com"></a>Model COM

Zawiera informacje dotyczące funkcji COM dla obiektu.

- **Coclass**

   Ustawia nazwę klasy składnika, który zawiera listę interfejsów, obsługiwane przez obiekt.

   > [!NOTE]
   > Jeśli tworzysz projekt za pomocą atrybutów lub jeśli na tej stronie kreatora wskazujesz, że na stronie właściwości używa atrybutów, nie można zmienić tej opcji, ponieważ nie ma ATL `coclass` atrybutu.

- **Typ**

   Określa opis obiektu, który będzie wyświetlany w rejestrze

- **ProgID**

   Ustawia nazwę, która kontenerów można użyć zamiast identyfikatora CLSID obiektu.

::: moniker-end

## <a name="see-also"></a>Zobacz także

[Opcje, Kreator strony właściwości ATL](../../atl/reference/options-atl-property-page-wizard.md)<br/>
[Ciągi, Kreator strony właściwości ATL](../../atl/reference/strings-atl-property-page-wizard.md)<br/>
[Przykład: implementowanie strony właściwości](../../atl/example-implementing-a-property-page.md)
