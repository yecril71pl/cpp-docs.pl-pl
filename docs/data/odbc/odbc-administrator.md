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
ms.openlocfilehash: 55b214ba3513f95533e3892fb93ad9298c44415d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090198"
---
# <a name="odbc-administrator"></a>Administrator ODBC
ODBC Administrator rejestruje i konfiguruje [źródeł danych](../../data/odbc/data-source-odbc.md) dostępne lokalnie lub w sieci. Kreatorzy Użyj informacji dostarczonych przez administratora ODBC, aby utworzyć kod w aplikacjach, które łączy użytkowników ze źródłami danych.  
  
 Aby skonfigurować źródła danych ODBC do użycia z klas MFC ODBC lub klas MFC obiekt DAO (Data Access), najpierw musisz zarejestrować i skonfiguruj źródło danych. ODBC Administrator umożliwia dodawanie i usuwanie źródeł danych. W zależności od sterownika ODBC można również utworzyć nowe źródła danych.  
  
 ODBC Administrator jest instalowana podczas instalacji. Jeśli została wybrana opcja **niestandardowy** instalacji i nie wybrano żadnych sterowników ODBC w **opcje bazy danych** okno dialogowe, należy uruchomić ponownie Instalatora, aby zainstalować potrzebne pliki.  
  
 Podczas instalacji można wybrać sterowniki ODBC, które chcesz zainstalować. Później można zainstalować dodatkowe sterowniki, które są dostarczane z programem Visual C++ przy użyciu Instalatora programu Visual C++.  
  
 Jeśli chcesz zainstalować sterowniki ODBC, które nie są dostarczane z programem Visual C++, należy uruchomić programu instalacyjnego, który towarzyszy sterownika.  
  
#### <a name="to-install-odbc-drivers-that-ship-with-visual-c"></a>Aby zainstalować sterowniki ODBC, które są dostarczane z programem Visual C++  
  
1.  Uruchom Instalatora z dysku CD dystrybucji Visual C++.  
  
     Otwarcie jest pojawi się okno dialogowe programu instalacyjnego.  
  
2.  Kliknij przycisk **dalej** dotyczące każdego okna dialogowego aż **opcje instalacji** okno dialogowe. Wybierz **niestandardowy**, a następnie kliknij przycisk `Next`.  
  
3.  Usuń zaznaczenie pól wyboru w **Instalator programu Microsoft Visual C++** okno dialogowe z wyjątkiem **opcje bazy danych** pole wyboru, a następnie kliknij przycisk **szczegóły** do wyświetlenia **Opcje bazy danych** okno dialogowe.  
  
4.  Wyczyść **Microsoft Data Access Objects** zaznacz pole wyboru **sterowniki ODBC firmy Microsoft** pole wyboru, a następnie kliknij przycisk **szczegóły**.  
  
     **Sterowniki ODBC firmy Microsoft** zostanie wyświetlone okno dialogowe.  
  
5.  Wybierz sterowniki, należy zainstalować, a następnie kliknij przycisk **OK** dwa razy.  
  
6.  Kliknij przycisk **dalej** w pozostałych oknach dialogowych, aby rozpocząć instalację. Instalator powiadamia po zakończeniu instalacji.  
  
 Podczas instalowania sterowników, można skonfigurować źródło danych za pomocą Administratora ODBC. Ikona ODBC można znaleźć w Panelu sterowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Otwórz połączenie z bazą danych (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)   
 [Źródło danych (ODBC)](../../data/odbc/data-source-odbc.md)