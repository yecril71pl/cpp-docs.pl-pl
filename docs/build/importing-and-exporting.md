---
title: Importowanie i eksportowanie
ms.date: 05/06/2019
helpviewer_keywords:
- DLLs [C++], importing
- exporting DLLs [C++]
- importing DLLs [C++]
- DLLs [C++], exporting from
- __declspec(dllimport) keyword [C++]
ms.assetid: 7c44c2aa-2117-4cec-9615-a65bfd3f8f7b
ms.openlocfilehash: 29c8abf9528c2c34bd918463bccc8f845958759c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231536"
---
# <a name="importing-and-exporting"></a>Importowanie i eksportowanie

Można zaimportować symbole publiczne do aplikacji lub wyeksportować funkcje z biblioteki DLL przy użyciu dwóch metod:

- Podczas kompilowania biblioteki DLL Użyj pliku definicji modułu (. def)

- Używanie słów kluczowych **`__declspec(dllimport)`** lub **`__declspec(dllexport)`** w definicji funkcji w aplikacji głównej

## <a name="using-a-def-file"></a>Przy użyciu pliku. def

Plik definicji modułu (. def) jest plikiem tekstowym zawierającym jedną lub więcej instrukcji modułu, które opisują różne atrybuty biblioteki DLL. Jeśli nie używasz **`__declspec(dllimport)`** lub **`__declspec(dllexport)`** do eksportowania funkcji biblioteki DLL, biblioteka DLL wymaga pliku. def.

Pliki. def można użyć do [zaimportowania do aplikacji](importing-using-def-files.md) lub [eksportu z biblioteki DLL](exporting-from-a-dll-using-def-files.md).

## <a name="using-__declspec"></a>Używanie __declspec

Nie trzeba używać **`__declspec(dllimport)`** do prawidłowego kompilowania kodu, ale dzięki temu kompilator może generować lepszy kod. Kompilator może generować lepszy kod, ponieważ może określić, czy funkcja istnieje w bibliotece DLL, co umożliwia kompilatorowi tworzenie kodu, który pomija poziom pośredni, który zwykle jest obecny w wywołaniu funkcji, która przekroczyła granicę biblioteki DLL. Należy jednak użyć, **`__declspec(dllimport)`** Aby zaimportować zmienne używane w bibliotece DLL.

W przypadku prawidłowej sekcji EKSPORTy plików. def **`__declspec(dllexport)`** nie jest wymagana. **`__declspec(dllexport)`** dodano, aby zapewnić łatwy sposób eksportowania funkcji z pliku exe lub dll bez użycia pliku. def.

Przenośny format wykonywalny Win32 został zaprojektowany w celu zminimalizowania liczby stron, które muszą być naprawione w celu naprawy. W tym celu umieszcza wszystkie adresy importu dla każdego programu w jednym miejscu nazywanym tabelą importu adresów. Pozwala to programowi ładującemu modyfikować tylko jedną lub dwie strony podczas uzyskiwania dostępu do tych importów.

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Importowanie do aplikacji](importing-into-an-application-using-declspec-dllimport.md)

- [Eksportuj z biblioteki DLL](exporting-from-a-dll.md)

## <a name="see-also"></a>Zobacz także

[Tworzenie bibliotek DLL C/C++ w programie Visual Studio](dlls-in-visual-cpp.md)
