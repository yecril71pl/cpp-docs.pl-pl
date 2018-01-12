---
title: "Błąd kompilatora zasobów RW2003 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: RW2003
dev_langs: C++
helpviewer_keywords: RW2003
ms.assetid: 9dc0ba70-6776-4aef-b316-5f1711d8e42e
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9f388ca21d95e7d675a6b9890a7368765b5c0d7e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-error-rw2003"></a>Błąd kompilatora zasobów RW2003
Błąd generowania  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny  
  
1.  **Błąd: Mapa bitowa pliku z pliku zasobu nie jest w formacie 3.00**  
  
     Mapy bitowe przy użyciu formatu 2.x wersji systemu Windows nie można używać w wersji 3.x zasobów plików. Mapa bitowa musi być narysowany ponownie lub konwertowana na 3.x format.  
  
2.  **Błąd: Stare DIB w Nazwa zasobu. Przekazuj SDKPAINT**  
  
     Niezależne mapy bitowej urządzenia (DIB) w określony zasób nie jest zgodny z formatem Windows 3.0. Mapa bitowa musi być narysowany ponownie lub konwertowana na format 3.x.  
  
3.  **Błąd: Nazwa zasobu zasobów plików nie jest w formacie 3.00**  
  
     Ikony lub kursora określonego zasobu używany format z poprzedniej wersji systemu Windows. Ikona lub kursor musi narysowany ponownie lub konwertowana na format 3.x.  
  
4.  **Nieznany format nagłówka DIB**  
  
     Nagłówek mapy bitowej nie jest BITMAPCOREHEADER lub BITMAPINFOHEADER struktury.  
  
5.  **Nie można zainicjować informacji o symbolach**  
  
     Ten błąd występuje tylko w programie Visual C++. Prawdopodobna przyczyna to ma zbyt wiele otwartych plików lub nie można otworzyć lub zapisać pliki danych wymagane dla programu Visual C++ do zaimportowania symbole w skrypcie. Visual C++ podejmuje próbę tworzenia tych plików w katalogu określonym przez **TMP** zmiennej środowiskowej lub jeśli nie określono bieżącego katalogu.  
  
6.  **Nie można zapisać informacji o symbolach**  
  
     Ten błąd występuje tylko w programie Visual C++. Prawdopodobna przyczyna to ma zbyt wiele otwartych plików lub nie można zamknąć lub zapisywanie do plików danych wymagane dla programu Visual C++ do zaimportowania symbole w skrypcie. Visual C++ podejmuje próbę użycia tych plików w katalogu określonym przez **TMP** zmiennej środowiskowej lub jeśli nie określono bieżącego katalogu.  
  
7.  **Plik zasobów pliku mapy bitowej nie jest w formacie 2.03**  
  
     Mapy bitowej używany format starszych niż w wersji 2.03. Mapa bitowa musi być skonwertowany lub ponownie wystawionych, w formacie w wersji 3.00 lub nowszej.  
  
8.  **Zasób za duży**  
  
     Dla systemu Windows 3.1 zasobu nie może przekraczać około 65000 bajtów. Jeśli zasób jest, następnie nie będzie mógł go skompilować z języka Visual C++ lub kompilatora wiersza polecenia zasobów. To ograniczenie nie ma zastosowania do kursory, ikony, map bitowych lub innych zasobów opartych na plikach.  
  
9. **Plik zasobu nie jest w formacie 3.00**  
  
     Kursora lub ikony starszych niż w wersji 3.00 używany format. Zasób musi być skonwertowany lub ponownie wystawionych, w formacie w wersji 3.00 lub nowszej.  
  
10. **Nie można otworzyć pliku tymczasowego**  
  
     Nie można otworzyć pliku tymczasowego zasobu kompilatora/Visual C++. Prawdopodobna przyczyna to, że katalog nie istnieje albo nie masz uprawnienia do zapisu dla katalogu. Zasób kompilatora/Visual C++ podejmuje próbę użycia tych plików w katalogu określonym przez **TMP** zmiennej środowiskowej lub jeśli nie określono bieżącego katalogu.