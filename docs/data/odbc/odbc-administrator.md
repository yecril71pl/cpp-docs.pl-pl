---
title: Administrator ODBC
ms.date: 11/04/2016
helpviewer_keywords:
- installing ODBC
- ODBC data sources [C++], ODBC Administrator
- ODBC drivers [C++], installing
- ODBC [C++], ODBC Administrator
- Administrator in ODBC
- administration ODBC Administrator
- ODBC Administrator [C++]
- drivers [C++], ODBC
ms.assetid: b8652790-3437-4e7d-bc83-6ea6981f008b
ms.openlocfilehash: ac893981ff8c697dc090f1e6ad5ac61886a69f99
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59035867"
---
# <a name="odbc-administrator"></a>Administrator ODBC

ODBC Administrator rejestruje i konfiguruje [źródeł danych](../../data/odbc/data-source-odbc.md) dostępne lokalnie lub w sieci. Kreatory korzystają informacje podane przez administratora ODBC do pisania kodu w aplikacjach, które łączy się użytkowników ze źródłami danych.

Aby skonfigurować źródła danych ODBC do użytku z klas MFC ODBC lub klas MFC obiekt DAO (Data Access), najpierw musisz zarejestrować i konfigurowanie źródła danych. Dodawanie i usuwanie źródeł danych, należy użyć konta administratora ODBC. W zależności od sterownik ODBC można również utworzyć nowe źródła danych.

ODBC Administrator jest instalowana podczas instalacji. Jeśli została wybrana opcja **niestandardowe** instalacji i nie wybrano wszystkie sterowniki ODBC w **opcje bazy danych** okno dialogowe, musisz uruchomić ponownie Instalatora, aby zainstalować wymagane pliki.

Podczas instalacji możesz wybrać sterowników ODBC, który chcesz zainstalować. Później można zainstalować dodatkowe sterowniki, które są dostarczane z programem Visual C++ przy użyciu Instalatora programu Visual C++.

Jeśli chcesz zainstalować sterowniki ODBC, które nie są dostarczane z programem Visual C++, należy uruchomić program instalacyjny, który towarzyszy sterownika.

#### <a name="to-install-odbc-drivers-that-ship-with-visual-c"></a>Aby zainstalować sterowniki ODBC, które są dostarczane z programem Visual C++

1. Uruchom Instalatora z dysku CD dystrybucji Visual C++.

   Otwieranie wydaje się okno dialogowe programu instalacyjnego.

1. Kliknij przycisk **dalej** dotyczące każdego okna dialogowego aż **opcje instalacji** okno dialogowe. Wybierz **niestandardowe**, a następnie kliknij przycisk **dalej**.

1. Usuń zaznaczenie wszystkich pól wyboru w **Instalator programu Microsoft Visual C++** okno dialogowe z wyjątkiem **opcje bazy danych** pole wyboru, a następnie kliknij przycisk **szczegóły** do wyświetlenia **Opcje bazy danych** okno dialogowe.

1. Wyczyść **Microsoft Data Access Objects** pole wyboru, wybierz opcję **sterowniki ODBC firmy Microsoft** pole wyboru, a następnie kliknij przycisk **szczegóły**.

   **Sterowniki ODBC firmy Microsoft** pojawi się okno dialogowe.

1. Wybierz sterowniki, należy zainstalować, a następnie kliknij przycisk **OK** dwa razy.

1. Kliknij przycisk **dalej** w pozostałych oknach dialogowych, aby rozpocząć instalację. Instalator powiadamia o zakończeniu instalacji.

Jeśli sterowniki zostały zainstalowane, można skonfigurować źródło danych przy użyciu Administratora ODBC. Ikona ODBC znajdzie się w Panelu sterowania.

## <a name="see-also"></a>Zobacz także

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Źródło danych (ODBC)](../../data/odbc/data-source-odbc.md)