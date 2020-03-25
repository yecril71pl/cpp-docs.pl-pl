---
title: Błąd kompilatora zasobów RW2003
ms.date: 11/04/2016
f1_keywords:
- RW2003
helpviewer_keywords:
- RW2003
ms.assetid: 9dc0ba70-6776-4aef-b316-5f1711d8e42e
ms.openlocfilehash: 60e813fff46ebc015f281dfed99d2916ca0eb4bb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190615"
---
# <a name="resource-compiler-error-rw2003"></a>Błąd kompilatora zasobów RW2003

Błąd generacji

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać ten problem, sprawdzając następujące możliwe przyczyny

1. **Błąd: plik mapy bitowej nie ma formatu 3,00**

   Mapy bitowe używające formatu systemu Windows w wersji 2. x nie mogą być używane w plikach zasobów w wersji 3. x. Mapa bitowa musi być odświeżana lub konwertowana na format 3. x.

1. **Błąd: stary format DIB w nazwie zasobu. Przekazuj za poorednictwem SDKPAINT**

   Mapa bitowa niezależna od urządzenia (DIB) w określonym zasobie jest niezgodna z formatem systemu Windows 3,0. Mapa bitowa musi być odświeżana lub konwertowana na format 3. x.

1. **Błąd: nazwa zasobu pliku zasobu nie jest w formacie 3,00**

   Ikona lub kursor w określonym zasobie używał formatu z poprzedniej wersji systemu Windows. Ikona lub kursor muszą zostać narysowane lub przekonwertowane na format 3. x.

1. **Nieznany format nagłówka DIB**

   Nagłówek mapy bitowej nie jest strukturą BITMAPCOREHEADER ani BITMAPINFOHEADER.

1. **Nie można zainicjować informacji o symbolach**

   Ten błąd występuje tylko w wizualizacji C++. Prawdopodobną przyczyną jest zbyt wiele otwartych plików lub nie można otwierać ani zapisywać plików danych wymaganych do wizualizacji C++ w celu zaimportowania symboli w skrypcie. Wizualizacja C++ próbuje utworzyć te pliki w katalogu określonym przez zmienną środowiskową **tmp** lub bieżącym katalogu, jeśli żaden nie został określony.

1. **Nie można zapisać informacji o symbolach**

   Ten błąd występuje tylko w wizualizacji C++. Prawdopodobną przyczyną jest zbyt wiele otwartych plików lub nie można zamknąć ani zapisywać plików danych wymaganych do wizualizacji C++ w celu zaimportowania symboli w skrypcie. Wizualizacja C++ próbuje użyć tych plików w katalogu określonym przez zmienną środowiskową **tmp** lub bieżącym katalogu, jeśli żaden nie został określony.

1. **Plik zasobów pliku mapy bitowej nie jest w formacie 2,03**

   Mapa bitowa używała formatu wcześniejszego niż wersja 2,03. Mapa bitowa musi być konwertowana lub ponownie narysowana przy użyciu formatu w wersji 3,00 lub nowszej.

1. **Zasób jest zbyt duży**

   W przypadku systemu Windows 3,1 zasób nie może przekroczyć około 65000 bajtów. Jeśli zasób nie będzie można skompilować za pomocą wizualizacji C++ lub kompilatora zasobów wiersza polecenia. Ten limit nie dotyczy kursorów, ikon, map bitowych ani innych zasobów opartych na plikach.

1. **Plik zasobów nie jest w formacie 3,00**

   Kursor lub ikona używały formatu starszej niż wersja 3,00. Zasób musi zostać skonwertowany lub ponownie narysowany przy użyciu formatu w wersji 3,00 lub nowszej.

1. **Nie można otworzyć pliku tymczasowego**

   Kompilator zasobów/Wizualizacja C++ nie mogła otworzyć pliku tymczasowego. Prawdopodobną przyczyną jest to, że nie masz uprawnień do zapisu w katalogu lub katalog nie istnieje. Kompilator zasobów/Wizualizacja C++ próbuje użyć tych plików w katalogu określonym przez zmienną środowiskową **tmp** lub bieżącym katalogu, jeśli żaden nie został określony.
