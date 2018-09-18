---
title: ODBC Administrator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c0a0c0cc8817d40b325ceb7a96769dfe971b60c8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097812"
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
  
## <a name="see-also"></a>Zobacz też  

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Źródło danych (ODBC)](../../data/odbc/data-source-odbc.md)