---
title: Błąd kompilatora zasobów RW2003 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW2003
dev_langs:
- C++
helpviewer_keywords:
- RW2003
ms.assetid: 9dc0ba70-6776-4aef-b316-5f1711d8e42e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f7b4341c4567e7a58135cc99a793f287f810043
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096785"
---
# <a name="resource-compiler-error-rw2003"></a>Błąd kompilatora zasobów RW2003

Błąd generowania

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny

1. **Błąd: Plik zasobów mapy bitowej pliku nie jest w formacie 3.00**

     Nie można używać mapy bitowej w formacie Windows w wersji 2.x pliki w wersji 3.x zasobów. Mapa bitowa musi być narysowany ponownie lub przekonwertowane na 3.x format.

1. **Błąd: Stare DIB w nazwie zasobu. Przekazuj SDKPAINT**

     Niezależnie od mapy bitowej urządzenia (DIB) w określonym zasobie nie jest zgodny z formatem Windows 3.0. Mapa bitowa musi być narysowany ponownie lub przekonwertowane na 3.x format.

1. **Błąd: Zasobów — Nazwa pliku zasobu nie jest w formacie 3.00**

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

9. **Plik zasobu nie jest w formacie 3.00**

     Kursor lub ikonę wcześniej niż w wersji 3.00 używany format. Zasób musi być przekonwertowany lub ponownie, wystawione przy użyciu formatu dla wersji 3.00 lub nowszej.

10. **Nie można otworzyć pliku tymczasowego**

     Nie można otworzyć pliku tymczasowego zasobu kompilatora/Visual C++. Prawdopodobna przyczyna to, że katalog nie istnieje albo nie masz uprawnień do zapisu dla katalogu. Zasób kompilatora/Visual C++ podejmują próbę użycia tych plików w katalogu określonym przez **TMP** zmiennej środowiskowej lub bieżącego katalogu, jeśli nie określono.