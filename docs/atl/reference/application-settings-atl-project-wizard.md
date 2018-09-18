---
title: Ustawienia aplikacji, ATL projektów Kreatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.appwiz.atl.com.appset
dev_langs:
- C++
helpviewer_keywords:
- ATL Project Wizard, application settings
ms.assetid: d48c9fc5-f439-49fd-884c-8bcfa7d52991
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4cff60e5316202842b2ee22c5c6ba10813839b5d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035854"
---
# <a name="application-settings-atl-project-wizard"></a>Ustawienia aplikacji, Kreator projektów ATL

Użyj **ustawienia aplikacji** strony Kreator projektu ATL projektować i dodawanie podstawowych funkcji do nowego projektu ATL.

## <a name="server-type"></a>Typ serwera

Wybierz jedną z trzech typów serwerów:

- **Biblioteka dołączana dynamicznie (DLL)**  

   Zaznacz, aby utworzyć serwer w procesie.

- **Plik wykonywalny (EXE)**  

   Zaznacz, aby utworzyć serwer lokalny poza procesem. Ta opcja nie umożliwia obsługi MFC lub modelu COM + 1.0. Nie zezwala na scalanie kodu klasy zastępczej/serwera proxy.

- **Usługa (EXE)**  

   Zaznacz, aby utworzyć aplikację Windows, która działa w tle podczas uruchamiania Windows. Ta opcja nie zezwala na obsługę MFC lub modelu COM + 1.0 lub nie zezwala na scalanie kodu klasy zastępczej/serwera proxy.

## <a name="additional-options"></a>Dodatkowe opcje

> [!NOTE]
> Wszystkie dodatkowe opcje są dostępne biblioteki DLL tylko dla projektów.

- **Zezwalaj na scalanie kodu klasy zastępczej/serwera proxy**  

   Wybierz **Zezwalaj na scalanie kodu klasy zastępczej/serwera proxy** pole wyboru dla wygody, gdy wymagana jest kierowanie interfejsów. Ta opcja umieszcza kod serwera proxy i klas zastępczych MIDL generowane w tym samym pliku wykonywalnego jako serwer.

- **Obsługa MFC**  

   Zaznacz, aby określić, że obiekt zawiera obsługę MFC. Ta opcja łączy projektu biblioteki MFC, aby dostęp do wszystkich klas i funkcji, które zawierają.

- **Obsługa modelu COM + 1.0**  

   Zaznacz, aby zmodyfikować ustawienia kompilacji projektu do obsługi składników modelu COM + 1.0. Oprócz standardowych listę bibliotek Kreator dodaje comsvcs.lib biblioteki specyficzne dla składników modelu COM + 1.0

   Ponadto mtxex.dll jest ładowane w systemie hosta, po uruchomieniu aplikacji z opóźnieniem.

- **Obsługa rejestratora składników**

   Projekt ATL zawiera wsparcie dla składników modelu COM + 1.0, po ustawieniu tej opcji. Rejestratora składników umożliwia obiektu modelu COM + 1.0 do uzyskiwania listy składników, rejestrować składników lub wyrejestrować komponenty (pojedynczo lub wszystkie na raz).

## <a name="see-also"></a>Zobacz też

[Kreator projektu ATL](../../atl/reference/atl-project-wizard.md)<br/>
[Tworzenie projektu ATL](../../atl/reference/creating-an-atl-project.md)<br/>
[Domyślne konfiguracje projektu ATL](../../atl/reference/default-atl-project-configurations.md)

