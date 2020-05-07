---
title: GetProcAddress
ms.date: 11/04/2016
f1_keywords:
- GetProcAddress
helpviewer_keywords:
- DLLs [C++], GetProcAddress
- ordinal exports [C++]
- GetProcAddress method
ms.assetid: 48d14ae0-47ea-4c5d-96b1-2c158f1a26af
ms.openlocfilehash: 2d322cfe7d3bd60d8d702a226e181eb7b4ede963
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493251"
---
# <a name="getprocaddress"></a>GetProcAddress

Procesy jawnie łączące się z wywołaniem DLL wywołania [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) w celu uzyskania adresu eksportowanej funkcji w bibliotece DLL. Aby wywołać funkcję DLL, należy użyć zwróconego wskaźnika funkcji. Funkcja **GetProcAddress** przyjmuje jako parametry obsługę modułu dll (zwracaną przez funkcję **LoadLibrary**lub `AfxLoadLibrary` **GetModuleHandle**) i pobiera nazwę funkcji, która ma zostać wywołana, lub numer porządkowy eksportu funkcji.

Ponieważ wywołujesz funkcję DLL za pomocą wskaźnika i nie ma sprawdzania typu w czasie kompilacji, upewnij się, że parametry funkcji są poprawne, aby nie przekroczyć pamięci przyłożonej na stos i spowodować naruszenie zasad dostępu. Jednym ze sposobów zapewnienia bezpieczeństwa typów jest wyszukanie prototypów funkcji eksportowanych funkcji i utworzenie zgodnych elementów typedef dla wskaźników funkcji. Przykład:

```
typedef UINT (CALLBACK* LPFNDLLFUNC1)(DWORD,UINT);
...

HINSTANCE hDLL;               // Handle to DLL
LPFNDLLFUNC1 lpfnDllFunc1;    // Function pointer
DWORD dwParam1;
UINT  uParam2, uReturnVal;

hDLL = LoadLibrary("MyDLL");
if (hDLL != NULL)
{
   lpfnDllFunc1 = (LPFNDLLFUNC1)GetProcAddress(hDLL,
                                           "DLLFunc1");
   if (!lpfnDllFunc1)
   {
      // handle the error
      FreeLibrary(hDLL);
      return SOME_ERROR_CODE;
   }
   else
   {
      // call the function
      uReturnVal = lpfnDllFunc1(dwParam1, uParam2);
   }
}
```

Sposób określania funkcji, która ma **być wywoływana, zależy od tego,** jak biblioteka DLL została skompilowana.

Można uzyskać tylko numer porządkowy eksportu, jeśli biblioteka DLL, z którą tworzysz łącze, jest skompilowana przy użyciu pliku definicji modułu (. def), a liczby porządkowe są wyświetlane z funkcjami w sekcji **eksporty** pliku dll. def. Wywoływanie funkcji **GetProcAddress** z numerem porządkowym eksportu, w przeciwieństwie do nazwy funkcja, jest nieco szybsze, jeśli biblioteka DLL ma wiele funkcji, ponieważ eksporty mogą pełnić rolę indeksów w tabeli eksportu biblioteki DLL. W przypadku liczby porządkowej eksportu funkcja **GetProcAddress** może zlokalizować funkcję bezpośrednio, zamiast porównywać określoną nazwę z nazwami funkcji w tabeli eksportu biblioteki DLL. Jednak należy wywołać funkcję **GetProcAddress** z numerem porządkowym eksportu tylko wtedy, gdy masz kontrolę nad przypisaniem porządkowych do eksportowanych funkcji w pliku. def.

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Łączenie pliku wykonywalnego z biblioteką DLL](linking-an-executable-to-a-dll.md#linking-implicitly)

- [Łączenie pliku wykonywalnego z biblioteką DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>Jak chcesz dowiedzieć się więcej?

- [LoadLibrary i AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)

- [FreeLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-freelibrary)

- [Eksportowanie z biblioteki DLL przy użyciu plików DEF](exporting-from-a-dll-using-def-files.md)

## <a name="see-also"></a>Zobacz też

[Tworzenie bibliotek DLL C/C++ w programie Visual Studio](dlls-in-visual-cpp.md)
