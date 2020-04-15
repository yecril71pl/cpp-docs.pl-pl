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
ms.openlocfilehash: a10c5c358901122dda37b395c1f0fa5cdc30ce30
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321698"
---
# <a name="atl-control-wizard"></a>Kreator kontrolki ATL

Wstawia do projektu ATL (lub projektu MFC z obsługą ATL) kontrolki ATL. Za pomocą tego kreatora można wstawić jeden z trzech rodzajów formantów:

- Sterowanie standardowe

- Sterowanie kompozytowe

- Kontrolka DHTML

Ponadto można określić minimalny formant, usuwając interfejsy z listy [Interfejsy,](../../atl/reference/interfaces-atl-control-wizard.md) które są dostarczane jako domyślne formanty do otwarcia w większości kontenerów. Interfejsy, które mają być obsługiwane dla formantu, można ustawić na stronie **Interfejsy** kreatora.

## <a name="remarks"></a>Uwagi

Skrypt rejestracji wyprodukowany przez tego kreatora zarejestruje swoje składniki COM w obszarze HKEY_CURRENT_USER zamiast HKEY_LOCAL_MACHINE. Aby zmodyfikować to zachowanie, należy ustawić **opcję Zarejestruj składnik dla wszystkich użytkowników** Kreatora ATL.

## <a name="names"></a>Nazwy

Określ nazwy obiektu, interfejsu i klas, które mają zostać dodane do projektu. Z wyjątkiem **krótkiej nazwy,** wszystkie inne pola mogą być zmieniane niezależnie. Jeśli zmienisz tekst **dla krótkiej nazwy,** zmiana zostanie odzwierciedlona w nazwach wszystkich innych pól na tej stronie. Jeśli zmienisz nazwę **Coclass** w sekcji COM, zmiana zostanie odzwierciedlona w polu **Typ,** ale nazwa **interfejsu** i **progid** nie ulegnie zmianie. To zachowanie nazewnictwa jest przeznaczony do wszystkich nazw łatwo rozpoznawalne dla Ciebie podczas rozwijania kontroli.

> [!NOTE]
> **Coclass** jest edytowalny tylko na formanty nonattributed. Jeśli projekt jest przypisany, nie można edytować **programu Coclass**.

### <a name="c"></a>C++

Zawiera informacje dla klasy C++ utworzonej w celu zaimplementowania obiektu.

- **Krótka nazwa**

   Ustawia skróconą nazwę obiektu. Podana nazwa określa nazwy klasy i **coclass,** plik (. CPP i . H) nazwy, nazwa interfejsu i **nazwy typu,** chyba że zmienisz te pola indywidualnie.

- **Klasa**

   Ustawia nazwę klasy, która implementuje obiekt. Ta nazwa jest oparta na nazwie podającej w **skróconej nazwie,** poprzedzonej "C", typowym prefiksem nazwy klasy.

- **.h plik**

   Ustawia nazwę pliku nagłówka dla klasy nowego obiektu. Domyślnie ta nazwa jest oparta na nazwie podajona w **skróconej nazwie**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji lub dołączyć deklarację klasy do istniejącego pliku. Jeśli wybierzesz istniejący plik, kreator nie zapisze go w wybranej lokalizacji, dopóki nie klikniesz **przycisku Zakończ**.

   Kreator nie zastępuje pliku. Jeśli wybierzesz nazwę istniejącego pliku, po kliknięciu **przycisku Zakończ**kreator wyświetli monit o wskazanie, czy deklaracja klasy powinna być dołączona do zawartości pliku. Kliknij **przycisk Tak,** aby dołączyć plik; Kliknij przycisk **Nie,** aby powrócić do kreatora i określić inną nazwę pliku.

- **.cpp**

   Ustawia nazwę pliku implementacji dla klasy nowego obiektu. Domyślnie ta nazwa jest oparta na nazwie podajona w **skróconej nazwie**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji. Plik nie zostanie zapisany w wybranej lokalizacji, dopóki nie klikniesz **przycisku Zakończ** w kreatorze.

   Kreator nie zastępuje pliku. Jeśli wybierzesz nazwę istniejącego pliku, po kliknięciu **przycisku Zakończ,** kreator wyświetli monit o wskazanie, czy implementacja klasy powinna być dołączona do zawartości pliku. Kliknij **przycisk Tak,** aby dołączyć plik; Kliknij przycisk **Nie,** aby powrócić do kreatora i określić inną nazwę pliku.

- **Przypisane**

   Wskazuje, czy obiekt używa atrybutów. Jeśli dodajesz obiekt do przypisanego projektu ATL, ta opcja jest zaznaczona i nie jest dostępna do zmiany. Oznacza to, że można dodać tylko przypisane obiekty do projektu utworzonego za pomocą obsługi atrybutów.

   Przypisany obiekt można dodać tylko do projektu ATL, który używa atrybutów. Jeśli wybierzesz tę opcję dla projektu ATL, który nie obsługuje atrybutów, kreator monituje o określenie, czy chcesz dodać obsługę atrybutów do projektu.

   Domyślnie wszystkie obiekty dodane po ustawieniu tej opcji są oznaczone jako przypisane (zaznaczone jest pole wyboru). To pole można wyczyścić, aby dodać obiekt, który nie używa atrybutów.

   Aby uzyskać więcej informacji, zobacz [Ustawienia aplikacji, Kreator projektu ATL](../../atl/reference/application-settings-atl-project-wizard.md) i [podstawowa mechanika atrybutów.](../../windows/basic-mechanics-of-attributes.md)

### <a name="com"></a>Model COM

Zawiera informacje o funkcjach COM dla obiektu.

- **Coclass**

   Ustawia nazwę klasy składnika zawierającej listę interfejsów obsługiwanych przez obiekt.

   > [!NOTE]
   > Jeśli projekt zostanie utworzony przy użyciu atrybutów lub jeśli na tej stronie kreatora zostanie wskazane, że formant używa atrybutów, nie można zmienić tej opcji, ponieważ atl nie zawiera atrybutu **coclass.**

- **Interfejs**

   Ustawia nazwę interfejsu dla obiektu. Domyślnie nazwa interfejsu jest poprzedzony "I".

- **Typ**

   Ustawia opis obiektu, który pojawi się w rejestrze

- **Progid**

   Ustawia nazwę, której kontenery mogą używać zamiast identyfikatora CLSID obiektu. To pole nie jest wypełniane automatycznie. Jeśli to pole nie zostanie wypełnić ręcznie, formant może nie być dostępny dla innych narzędzi. Na przykład formanty ActiveX, `ProgID` które są generowane bez a nie są dostępne w oknie dialogowym **Wstawianie formantów ActiveX.** Aby uzyskać więcej informacji o oknie dialogowym, zobacz [Okno dialogowe Wstawianie formantu ActiveX](../../windows/insert-activex-control-dialog-box.md).

## <a name="see-also"></a>Zobacz też

[Sterowanie ATL](../../atl/reference/adding-an-atl-control.md)<br/>
[Dodawanie funkcji do kontrolki złożonej](../../atl/adding-functionality-to-the-composite-control.md)<br/>
[Podstawy obiektów ATL COM](../../atl/fundamentals-of-atl-com-objects.md)
