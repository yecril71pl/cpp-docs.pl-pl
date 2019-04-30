---
title: Błąd kompilatora zasobów RW2003
ms.date: 11/04/2016
f1_keywords:
- RW2003
helpviewer_keywords:
- RW2003
ms.assetid: 9dc0ba70-6776-4aef-b316-5f1711d8e42e
ms.openlocfilehash: f359c1f71f03ce0d946579776230398fb31d046f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396787"
---
# <a name="resource-compiler-error-rw2003"></a>Błąd kompilatora zasobów RW2003

Błąd generowania

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny

1. **Błąd: Mapa bitowa plik z pliku zasobów nie jest w formacie 3.00**

   Nie można używać mapy bitowej w formacie Windows w wersji 2.x pliki w wersji 3.x zasobów. Mapa bitowa musi być narysowany ponownie lub przekonwertowane na 3.x format.

1. **Błąd: Stary DIB w nazwie zasobu. Przekazuj SDKPAINT**

   Niezależnie od mapy bitowej urządzenia (DIB) w określonym zasobie nie jest zgodny z formatem Windows 3.0. Mapa bitowa musi być narysowany ponownie lub przekonwertowane na 3.x format.

1. **Błąd: Zasób — Nazwa pliku zasobu nie jest w formacie 3.00**

   Ikony lub kursora w określonym zasobie używany format z poprzedniej wersji systemu Windows. Ikony lub kursor musi odświeżać lub konwertowana na format 3.x.

1. **Nieznany format nagłówka DIB**

   Nagłówek mapa bitowa nie jest BITMAPCOREHEADER lub BITMAPINFOHEADER struktury.

1. **Nie można zainicjować informacji o symbolach**

   Ten błąd występuje tylko w języku Visual C++. Prawdopodobna przyczyna to, że zawiera zbyt wiele otwartych plików, lub nie można otworzyć lub zapisać pliki danych potrzebne do importowania symboli w skrypcie języka Visual C++. Visual C++ podejmuje próbę utworzenia tych plików w katalogu określonym przez **TMP** zmiennej środowiskowej lub bieżącego katalogu, jeśli nie określono.

1. **Nie można zapisać informacji o symbolach**

   Ten błąd występuje tylko w języku Visual C++. Prawdopodobna przyczyna to, że zawiera zbyt wiele otwartych plików, lub nie można zamknąć lub zapis w plikach danych potrzebne do importowania symboli w skrypcie języka Visual C++. Visual C++ podejmują próbę użycia tych plików w katalogu określonym przez **TMP** zmiennej środowiskowej lub bieżącego katalogu, jeśli nie określono.

1. **Mapa bitowa plik zasobu nie jest w formacie 2.03**

   Mapy bitowej używany format starszych niż w wersji 2.03. Mapa bitowa musi być przekonwertowany lub ponownie, wystawione przy użyciu formatu dla wersji 3.00 lub nowszej.

1. **Zasób za duży**

   Dla Windows 3.1 zasobu nie może przekroczyć około 65000 bajtów. Jeśli zasób jest, następnie nie można skompilować je przy użyciu języka Visual C++ i kompilator zasobów wiersza polecenia. To ograniczenie nie ma zastosowania do kursorów, ikony, mapy bitowe lub inne zasoby oparte na plikach.

1. **Plik zasobu nie jest w formacie 3.00**

   Kursor lub ikonę wcześniej niż w wersji 3.00 używany format. Zasób musi być przekonwertowany lub ponownie, wystawione przy użyciu formatu dla wersji 3.00 lub nowszej.

1. **Nie można otworzyć pliku tymczasowego**

   Nie można otworzyć pliku tymczasowego zasobu kompilatora/Visual C++. Prawdopodobna przyczyna to, że katalog nie istnieje albo nie masz uprawnień do zapisu dla katalogu. Zasób kompilatora/Visual C++ podejmują próbę użycia tych plików w katalogu określonym przez **TMP** zmiennej środowiskowej lub bieżącego katalogu, jeśli nie określono.