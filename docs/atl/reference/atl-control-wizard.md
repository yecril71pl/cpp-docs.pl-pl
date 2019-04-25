---
title: Kreator kontrolki ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.control.overview
helpviewer_keywords:
- ATL projects, adding controls
- controls [ATL], adding to projects
- ATL Control Wizard
ms.assetid: 991f8e72-ffbc-4382-a4ce-e255acfba5b6
ms.openlocfilehash: 58c3ebe4c2a15aa3f0d59191c37a7f2422a63ab5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62261211"
---
# <a name="atl-control-wizard"></a>Kreator kontrolki ATL

Operacje wstawiania do projektu ATL (lub projektu MFC z obsługą ATL) kontrolki ATL. Można użyć tego kreatora, aby wstawić jeden z trzech rodzajów formantów:

- Formantu standardowego

- Kontrolek złożonych

- Kontrolki DHTML

Ponadto można określić minimalnej kontrolki, usuwanie interfejsów z [interfejsów](../../atl/reference/interfaces-atl-control-wizard.md) listy, które są udostępniane jako domyślne dla formantów, które można otworzyć w większości kontenerów. Możesz ustawić interfejsy mają być obsługiwane dla formantu w **interfejsów** strony kreatora.

## <a name="remarks"></a>Uwagi

Skrypt rejestrowania generowane przez ten kreator zarejestruje jego składników modelu COM w gałęzi HKEY_CURRENT_USER zamiast HKEY_LOCAL_MACHINE. Aby zmienić to zachowanie, ustaw **części rejestru dla wszystkich użytkowników** opcji kreatora ATL.

## <a name="names"></a>Nazwy

Określ nazwy dla obiektu, interfejsów i klas, które mają zostać dodane do projektu. Z wyjątkiem **krótką nazwę**, wszystkie inne pola, które mogą być zmieniane niezależnie. Jeśli zmienisz tekst **krótką nazwę**, zmiany są widoczne w nazwach wszystkie inne pola na tej stronie. W przypadku zmiany **Coclass** nazwę w sekcji COM, zmiana jest odzwierciedlana w **typu** pola, ale **interfejsu** nazwy i **ProgID** czy Nie zmieniaj. To zachowanie nazewnictwa zaprojektowaną do podejmowania wszystkich nazw można łatwo zidentyfikować dla Ciebie podczas tworzenia kontrolki.

> [!NOTE]
>  **Klasa coclass** można edytować tylko nonattributed kontrolek. Jeśli projekt jest przypisane, nie można edytować **Coclass**.

### <a name="c"></a>C++

Zawiera informacje dla klasy języka C++ utworzona w celu wdrożenia obiektu.

- **Krótka nazwa**

   Ustawia skróconą nazwę dla obiektu. Należy podać nazwę określa klasę i **Coclass** nazywa plik (. CPP i. H) nazw, nazwę interfejsu i **typu** nazwy, chyba że zmienił się tych pól indywidualnie.

- **Class**

   Ustawia nazwę klasy, która implementuje obiektu. Ta nazwa jest oparta na nazwę, która zapewnia w **krótką nazwę**, poprzedzającą "C", typowy prefiks dla nazwy klasy.

- **plik .h**

   Określa nazwę pliku nagłówkowego klasy nowego obiektu. Domyślnie ta nazwa opiera się na nazwę, która zapewnia w **krótką nazwę**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku na lokalizację lub dołączyć deklaracji klasy do istniejącego pliku. Jeśli wybierzesz istniejący plik, Kreator nie zapisze go w wybranej lokalizacji do momentu kliknij **Zakończ**.

   Kreator nie powoduje zastąpienia pliku. Jeśli wybierasz nazwę istniejącego pliku, po kliknięciu **Zakończ**, Kreator wyświetli monit o wskazują, czy deklaracja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** można dołączyć pliku kliknij przycisk **nie** aby powrócić do kreatora i podaj inną nazwę pliku.

- **Plik CPP**

   Określa nazwę pliku implementacji dla nowego obiektu klasy. Domyślnie ta nazwa opiera się na nazwę, która zapewnia w **krótką nazwę**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji. Plik nie jest zapisywany w wybranej lokalizacji, dopóki nie klikniesz **Zakończ** w kreatorze.

   Kreator nie powoduje zastąpienia pliku. Jeśli wybierasz nazwę istniejącego pliku, po kliknięciu **Zakończ**, Kreator wyświetli monit o wskazują, czy Implementacja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** można dołączyć pliku kliknij przycisk **nie** aby powrócić do kreatora i podaj inną nazwę pliku.

- **Opartego na atrybutach**

   Wskazuje, czy obiekt używa atrybutów. W przypadku dodawania obiektu do projekcie ATL z atrybutami, ta opcja jest zaznaczone i nie można zmienić. Oznacza to, że można dodać tylko opartego na atrybutach obiekty do projektu utworzonego za pomocą atrybutu pomocy technicznej.

   Obiekt opartego na atrybutach można dodać tylko do projektu ATL, który używa atrybutów. Jeśli wybierzesz tę opcję, aby Projekt ATL, który nie ma atrybutu pomocy technicznej, w kreatora zostanie wyświetlony monit o określenie, czy chcesz dodać obsługę atrybutu do projektu.

   Domyślnie wszystkie obiekty, które możesz dodać po ustawieniu tej opcji są oznaczone jako opartego na atrybutach (pole wyboru jest zaznaczone). Aby wyczyścić to pole, aby dodać obiekt, który nie korzysta z atrybutów.

   Zobacz [ustawienia aplikacji, Kreator projektów ATL](../../atl/reference/application-settings-atl-project-wizard.md) i [podstawowa mechanika atrybutów](../../windows/basic-mechanics-of-attributes.md) Aby uzyskać więcej informacji.

### <a name="com"></a>Model COM

Zawiera informacje dotyczące funkcji COM dla obiektu.

- **Coclass**

   Ustawia nazwę klasy składnika, który zawiera listę interfejsów, obsługiwane przez obiekt.

   > [!NOTE]
   > Jeśli tworzysz projekt za pomocą atrybutów lub jeśli na tej stronie kreatora wskazujesz, że kontrolka używa atrybutów, nie można zmienić tej opcji, ponieważ nie ma ATL **coclass** atrybutu.

- **Interface**

   Ustawia nazwę interfejsu dla obiektu. Domyślnie nazwa interfejsu jest poprzedzona przedrostkiem "I".

- **Typ**

   Określa opis obiektu, który będzie wyświetlany w rejestrze

- **ProgID**

   Ustawia nazwę, która kontenerów można użyć zamiast identyfikatora CLSID obiektu. To pole nie jest automatycznie wypełnione. Jeśli to pole nie ręcznie wypełnić formant nie może być dostępne dla innych narzędzi. Na przykład formanty ActiveX, które są generowane, bez `ProgID` nie są dostępne w **Wstawianie formantu ActiveX** okno dialogowe. Aby uzyskać więcej informacji na temat okna dialogowego, zobacz [okno dialogowe Wstawianie kontrolki ActiveX](../../windows/insert-activex-control-dialog-box.md).

## <a name="see-also"></a>Zobacz także

[Kontrolka ATL](../../atl/reference/adding-an-atl-control.md)<br/>
[Dodawanie funkcji do kontrolek złożonych](../../atl/adding-functionality-to-the-composite-control.md)<br/>
[Podstawowe informacje na temat obiektów COM ATL](../../atl/fundamentals-of-atl-com-objects.md)
