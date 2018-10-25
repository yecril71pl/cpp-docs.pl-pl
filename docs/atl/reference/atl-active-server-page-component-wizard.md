---
title: Kreator składników stron Active Server ATL | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.asp.overview
dev_langs:
- C++
helpviewer_keywords:
- ASP components, creating in ATL
- ATL Active Server Page Component Wizard
ms.assetid: 5a5cb904-dbbf-44ea-ad3d-2ddd14c1d3c5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8a87b2ba1e846ce995a987379ae6f30567a39773
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053815"
---
# <a name="atl-active-server-page-component-wizard"></a>Kreator składników stron Active Server ATL

Ten kreator umożliwia wstawienie do projektu składnika strony Active Server Pages (ASP). Microsoft Internet Information Services (IIS) używa składników ASP jako część jego architekturę rozwoju udoskonalone strony sieci Web.

Za pomocą tego kreatora, można określić, że składnik w wielowątkowości, modelu i jego obsługa agregacji. Można również określić obsługę interfejsu informacje o błędzie, punkty połączenia i bezwątkowy szeregowanie.

> [!WARNING]
> W programie Visual Studio 2017 w wersji 15.9 tego kreatora kodu jest przestarzały i zostanie usunięta w przyszłych wersjach programu Visual Studio. Ten kreator jest rzadko używana. Ogólna obsługa biblioteki ATL i MFC nie ulega zmianie poprzez usunięcie tego kreatora. Jeśli chcesz przekazać opinię dotyczącą tego wycofywania, wypełnij [w ramach tej ankiety](https://www.surveymonkey.com/r/QDWKKCN). Twoja opinia ma znaczenie dla nas.

## <a name="remarks"></a>Uwagi

Począwszy od programu Visual Studio 2008, skrypt rejestrowania generowane przez kreatora, będą rejestrować jego składników modelu COM, w obszarze **HKEY_CURRENT_USER** zamiast **HKEY_LOCAL_MACHINE**. Aby zmienić to zachowanie, ustaw **części rejestru dla wszystkich użytkowników** opcji kreatora ATL.

## <a name="names"></a>Nazwy

Określ nazwy dla obiektu, interfejsów i klas, które mają zostać dodane do projektu. Z wyjątkiem **krótką nazwę**, wszystkie pozostałe pola mogą być edytowane, niezależnie od innych. Jeśli zmienisz tekst **krótką nazwę**, zmiany są widoczne w nazwach wszystkie inne pola na tej stronie.

Jeśli zmienisz **Coclass** nazwę w sekcji COM, zmiana jest odzwierciedlana w **typu** i **ProgID** pola, ale **interfejsu** nazwy nie zmienia się. To zachowanie nazewnictwa zaprojektowaną do podejmowania wszystkich nazw można łatwo zidentyfikować dla Ciebie podczas tworzenia kontrolki.

### <a name="c"></a>C++

Zawiera informacje dla klasy języka C++ utworzona dla obiektu.

- **Krótka nazwa**

   Określa nazwę katalogu głównego dla obiektu. Nazwy, zapewniające Określa `Class` i **Coclass** nazwy, **plik .cpp** i **plik .h klasy** nazwy, **interfejsu**nazwy **typu** nazwy i **ProgID**, chyba że zmienił się tych pól indywidualnie.

- **plik .h**

   Określa nazwę pliku nagłówkowego klasy nowego obiektu. Domyślnie ta nazwa opiera się na nazwę, która zapewnia w **krótką nazwę**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku na lokalizację lub dołączyć deklaracji klasy do istniejącego pliku. Jeśli wybierzesz istniejący plik, Kreator nie zapisze go w wybranej lokalizacji do momentu kliknij **Zakończ** w kreatorze.

   Kreator nie powoduje zastąpienia pliku. Jeśli wybierasz nazwę istniejącego pliku, po kliknięciu **Zakończ**, Kreator wyświetli monit o wskazują, czy deklaracja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** można dołączyć pliku kliknij przycisk **nie** aby powrócić do kreatora i podaj inną nazwę pliku.

- **Class**

   Ustawia nazwę klasy, która ma zostać utworzony. Ta nazwa jest oparta na nazwę, która zapewnia w **krótką nazwę**, poprzedzającą "C", typowy prefiks dla nazwy klasy.

- **Plik CPP**

   Określa nazwę pliku implementacji dla nowego obiektu klasy. Domyślnie ta nazwa opiera się na nazwę, która zapewnia w **krótką nazwę**. Kliknij przycisk wielokropka, aby zapisać nazwę pliku w wybranej lokalizacji. Plik nie jest zapisywany w wybranej lokalizacji, dopóki nie klikniesz **Zakończ** w kreatorze.

   Kreator nie powoduje zastąpienia pliku. Jeśli wybierasz nazwę istniejącego pliku, po kliknięciu **Zakończ**, Kreator wyświetli monit o wskazują, czy Implementacja klasy powinna zostać dołączona do zawartości pliku. Kliknij przycisk **tak** można dołączyć pliku kliknij przycisk **nie** aby powrócić do kreatora i podaj inną nazwę pliku.

- **Opartego na atrybutach**

   Wskazuje, czy obiekt używa atrybutów. W przypadku dodawania obiektu do projekcie ATL z atrybutami, ta opcja jest zaznaczone i nie można zmienić. Oznacza to, że można dodać tylko opartego na atrybutach obiekty do projektu utworzonego za pomocą atrybutu pomocy technicznej.

   Jeśli wybierzesz tę opcję, aby Projekt ATL, który nie ma atrybutu pomocy technicznej, w kreatora zostanie wyświetlony monit o określenie, czy chcesz dodać obsługę atrybutu do projektu.

   Domyślnie w przypadku projektów nonattributed wszystkie obiekty, które możesz dodać po ustawieniu tej opcji są oznaczone jako opartego na atrybutach (pole wyboru jest zaznaczone). Aby wyczyścić to pole, aby dodać obiekt, który nie korzysta z atrybutów.

   Zobacz [ustawienia aplikacji, Kreator projektów ATL](../../atl/reference/application-settings-atl-project-wizard.md) i [podstawowa mechanika atrybutów](../../windows/basic-mechanics-of-attributes.md) Aby uzyskać więcej informacji.

### <a name="com"></a>Model COM

Zawiera informacje dotyczące funkcji COM dla obiektu.

- **Klasa coclass**

   Ustawia nazwę klasy składnika, który zawiera listę interfejsów, obsługiwane przez obiekt. Jeśli projekt lub ten obiekt korzysta z atrybutów, nie można zmienić tej opcji, ponieważ nie ma ATL **coclass** atrybutu.

- **Typ**

   Określa opis obiektu, który będzie wyświetlany w rejestrze dla klasy coclass.

- **Interface**

   Ustawia interfejs, który można utworzyć obiektu. Ten interfejs zawiera swoje niestandardowe metody.

- **Identyfikator programu**

   Ustawia nazwę, która kontenerów można użyć zamiast identyfikatora CLSID obiektu.

## <a name="see-also"></a>Zobacz też

[Składnika strony Active Server ATL](../../atl/reference/adding-an-atl-active-server-page-component.md)
