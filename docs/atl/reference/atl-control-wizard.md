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
ms.openlocfilehash: c89fe17272399212e4436481abc2800c3ab6e660
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2020
ms.locfileid: "91353145"
---
# <a name="atl-control-wizard"></a>Kreator kontrolki ATL

Wstawia do projektu ATL (lub projektu MFC z obsługą ATL) formant ATL. Za pomocą tego kreatora można wstawić jeden z trzech rodzajów kontrolek:

- Kontrolka standardowa

- Formant złożony

- Kontrolka DHTML

Ponadto można określić minimalną kontrolę, usuwając interfejsy z listy [interfejsy](../../atl/reference/interfaces-atl-control-wizard.md) , które są dostępne jako ustawienia domyślne dla kontrolek do otwarcia w większości kontenerów. Interfejsy, które mają być obsługiwane dla formantu, można ustawić na stronie **interfejsy** kreatora.

## <a name="remarks"></a>Uwagi

Skrypt rejestracji utworzony przez tego kreatora zarejestruje jego składniki COM w HKEY_CURRENT_USER, a nie HKEY_LOCAL_MACHINE. Aby zmienić to zachowanie, ustaw opcję **Zarejestruj składnik dla wszystkich użytkowników** w Kreatorze ATL.

## <a name="names"></a>Nazwy

Określ nazwy obiektu, interfejsu i klas, które mają zostać dodane do projektu. Oprócz **krótkiej nazwy**wszystkie inne pola można zmieniać niezależnie. Jeśli zmienisz tekst **skróconej nazwy**, zmiana zostanie odzwierciedlona w nazwach wszystkich innych pól na tej stronie. Jeśli zmienisz nazwę **klasy coclass** w sekcji com, zmiana zostanie odzwierciedlona w polu **typ** , ale nazwa **interfejsu** i **ProgID** nie zostaną zmienione. Takie zachowanie nazewnictwa zostało zaprojektowane, aby wszystkie nazwy były łatwo rozpoznawalne podczas tworzenia kontrolki.

> [!NOTE]
> **Klasy coclass** można edytować tylko w kontrolkach niebędących atrybutami. Jeśli projekt nie jest przypisany, nie można edytować **klasy coclass**.

### <a name="c"></a>C++

Zawiera informacje dotyczące klasy języka C++, która została utworzona w celu zaimplementowania obiektu.

- **Krótka nazwa**

   Ustawia skróconą nazwę obiektu. Nazwa, która jest dostarczana określa klasy i nazwy klas **klasy** , pliku (. CPP i. H) nazwy, nazwy interfejsu i nazwy **typów** , chyba że te pola są zmieniane pojedynczo.

- **Klasa**

   Ustawia nazwę klasy implementującej obiekt. Ta nazwa jest oparta na nazwie, którą podano w **krótkiej nazwie**, poprzedzonej znakiem "C", typowym prefiksem dla nazwy klasy.

- **plik h**

   Ustawia nazwę pliku nagłówka dla klasy nowego obiektu. Domyślnie ta nazwa jest oparta na nazwie podanym w polu **krótka nazwa**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji, lub dołączyć deklarację klasy do istniejącego pliku. Jeśli wybierzesz istniejący plik, Kreator nie zapisze go w wybranej lokalizacji, dopóki nie klikniesz przycisku **Zakończ**.

   Kreator nie zastępuje pliku. Jeśli wybierzesz nazwę istniejącego pliku, po kliknięciu przycisku **Zakończ**Kreator monituje o wskazanie, czy deklaracja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** , aby dołączyć plik; Kliknij przycisk **nie** , aby powrócić do kreatora i określić inną nazwę pliku.

- **plik. cpp**

   Ustawia nazwę pliku implementacji dla klasy nowego obiektu. Domyślnie ta nazwa jest oparta na nazwie podanym w polu **krótka nazwa**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji. Plik nie jest zapisywany w wybranej lokalizacji, dopóki nie zostanie kliknięty przycisk **Zakończ** w kreatorze.

   Kreator nie zastępuje pliku. W przypadku wybrania nazwy istniejącego pliku po kliknięciu przycisku **Zakończ**Kreator monituje o wskazanie, czy implementacja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** , aby dołączyć plik; Kliknij przycisk **nie** , aby powrócić do kreatora i określić inną nazwę pliku.

- **Przypisanych**

   Wskazuje, czy obiekt używa atrybutów. Jeśli dodajesz obiekt do projektu ATL z atrybutami, ta opcja jest zaznaczona i nie można jej zmienić. Oznacza to, że można dodawać tylko obiekty z atrybutami do projektu utworzonego za pomocą obsługi atrybutu.

   Obiekt atrybutu można dodać tylko do projektu ATL, który używa atrybutów. W przypadku wybrania tej opcji dla projektu ATL, który nie obsługuje atrybutu, Kreator poprosi o określenie, czy chcesz dodać obsługę atrybutu do projektu.

   Domyślnie wszystkie obiekty dodane po ustawieniu tej opcji są oznaczone jako przypisane do atrybutu (pole wyboru jest zaznaczone). Możesz wyczyścić to pole, aby dodać obiekt, który nie używa atrybutów.

   Aby uzyskać więcej informacji [, zobacz Ustawienia aplikacji, Kreator projektu ATL](../../atl/reference/application-settings-atl-project-wizard.md) i [podstawowe Mechanics atrybutów](../../windows/attributes/cpp-attributes-com-net.md#basic-mechanics-of-attributes) .

### <a name="com"></a>Model COM

Zawiera informacje o funkcji COM dla obiektu.

- **Klasa coclass**

   Ustawia nazwę klasy składnika, która zawiera listę interfejsów obsługiwanych przez obiekt.

   > [!NOTE]
   > Jeśli tworzysz projekt przy użyciu atrybutów lub wskażesz na tej stronie kreatora, że formant używa atrybutów, nie można zmienić tej opcji, ponieważ ATL nie zawiera atrybutu **coclass** .

- **Interfejs**

   Ustawia nazwę interfejsu dla obiektu. Domyślnie nazwa interfejsu jest poprzedzona "I".

- **Typ**

   Ustawia opis obiektu, który będzie wyświetlany w rejestrze

- **ProgID**

   Ustawia nazwę, która może być używana przez kontenery zamiast identyfikatora CLSID obiektu. To pole nie jest wypełniane automatycznie. Jeśli to pole nie zostanie wypełnione ręcznie, kontrolka może nie być dostępna w innych narzędziach. Na przykład kontrolki ActiveX, które są generowane bez programu, `ProgID` nie są dostępne w oknie dialogowym **Wstawianie kontrolki ActiveX** . Aby uzyskać więcej informacji na temat okna dialogowego, zobacz [Wstawianie kontrolek ActiveX](../../windows/adding-editing-or-deleting-controls.md#insert-activex-controls).

## <a name="see-also"></a>Zobacz też

[Formant ATL](../../atl/reference/adding-an-atl-control.md)<br/>
[Dodawanie funkcji do kontrolki złożonej](../../atl/adding-functionality-to-the-composite-control.md)<br/>
[Podstawowe informacje o obiektach COM ATL](../../atl/fundamentals-of-atl-com-objects.md)
