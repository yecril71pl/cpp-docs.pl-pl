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
ms.openlocfilehash: 9e88492919eac80a4f3db2f94202d49011aa69de
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213190"
---
# <a name="odbc-administrator"></a>Administrator ODBC

Administrator ODBC rejestruje i konfiguruje [źródła danych](../../data/odbc/data-source-odbc.md) dostępne lokalnie lub przez sieć. Kreatorzy używają informacji dostarczonych przez administratora ODBC do tworzenia kodu w aplikacjach, które łączą użytkowników ze źródłami danych.

Aby skonfigurować źródło danych ODBC do użycia z klasami MFC ODBC lub klasami obiektów dostępu do danych MFC (DAO), należy najpierw zarejestrować i skonfigurować źródło danych. Dodawanie i usuwanie źródeł danych przy użyciu Administratora ODBC. W zależności od sterownika ODBC można także utworzyć nowe źródła danych.

Administrator ODBC jest instalowany podczas instalacji. Jeśli wybrano opcję Instalacja **niestandardowa** i nie wybrano żadnych sterowników ODBC w oknie dialogowym **Opcje bazy danych** , należy ponownie uruchomić Instalatora, aby zainstalować wymagane pliki.

Podczas instalacji należy wybrać sterowniki ODBC, które mają zostać zainstalowane. Możesz później zainstalować dodatkowe sterowniki dostarczane z wizualizacją C++ przy użyciu programu instalacyjnego C++ wizualizacji.

Jeśli chcesz zainstalować sterowniki ODBC, które nie są dostarczane z wizualizacją C++, musisz uruchomić program instalacyjny, który jest dołączony do sterownika.

#### <a name="to-install-odbc-drivers-that-ship-with-visual-c"></a>Aby zainstalować sterowniki ODBC dostarczane z wizualizacjąC++

1. Uruchom Instalatora z dysku dystrybucyjnego wizualizacji C++ .

   Zostanie wyświetlone okno dialogowe Otwieranie w programie instalacyjnym.

1. Kliknij przycisk **dalej** w każdym oknie dialogowym, dopóki nie zostanie wyświetlone okno dialogowe **Opcje instalacji** . Wybierz pozycję **niestandardowa**, a następnie kliknij przycisk **dalej**.

1. Wyczyść wszystkie pola wyboru w oknie dialogowym **Microsoft Visual C++ Setup** , z wyjątkiem pola wyboru **baza danych** , a następnie kliknij przycisk **szczegóły** , aby wyświetlić okno dialogowe **Opcje bazy danych** .

1. Wyczyść pole wyboru **Microsoft Data Access Objects** , zaznacz pole wyboru **sterowniki ODBC firmy Microsoft** , a następnie kliknij przycisk **szczegóły**.

   Zostanie wyświetlone okno dialogowe **sterowniki ODBC firmy Microsoft** .

1. Wybierz sterowniki, które chcesz zainstalować, a następnie kliknij przycisk **OK** dwa razy.

1. Kliknij przycisk **dalej** w pozostałych oknach dialogowych, aby rozpocząć instalację. Instalator powiadamia o zakończeniu instalacji.

Po zainstalowaniu sterowników można skonfigurować źródło danych za pomocą administratora ODBC. Ikona ODBC znajduje się w panelu sterowania.

## <a name="see-also"></a>Zobacz też

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Źródło danych (ODBC)](../../data/odbc/data-source-odbc.md)
