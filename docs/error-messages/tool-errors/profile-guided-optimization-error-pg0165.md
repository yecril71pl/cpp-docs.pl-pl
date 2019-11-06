---
title: Błąd optymalizacji opartej na profilach PG0165
description: Opisuje błędy PG0165 podczas odczytywania danych optymalizacji opartej na profilach (PGO).
ms.date: 10/30/2019
f1_keywords:
- PG0165
helpviewer_keywords:
- PG0165
ms.assetid: e98122e7-ddee-4a2c-96b2-d232e4c65f3e
ms.openlocfilehash: c5e5c5d37f8c70a6c2a3d9f7a43c13bb46d0e25a
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626802"
---
# <a name="profile-guided-optimization-error-pg0165"></a>Błąd optymalizacji opartej na profilach PG0165

Wystąpił błąd podczas odczytywania danych optymalizacji z przewodnikiem. Ten błąd może pojawić się w kilku formach:

> Odczytywanie*pliku "filename. PGD*": "wersja PGD nie jest obsługiwana (niezgodność wersji)".

Pliki PGD są specyficzne dla określonego zestawu narzędzi kompilatora. Ten błąd jest generowany, gdy używasz innego kompilatora niż ten, który został użyty do utworzenia *pliku filename. PGD*. Błąd oznacza, że ten zestaw narzędzi kompilatora nie może użyć danych z *pliku filename. PGD* do optymalizacji bieżącego programu. Aby rozwiązać ten problem, należy ponownie wygenerować *plik NazwaPliku*. PGD przy użyciu bieżącego zestawu narzędzi kompilatora.

> Odczytywanie pliku "*filename. PGD*": "plik PGD jest tylko do odczytu".

Ten błąd jest wyświetlany, gdy plik PGD jest oznaczony jako tylko do odczytu w systemie plików. Aby rozwiązać ten problem, Zmień atrybuty pliku na odczyt i zapis.
