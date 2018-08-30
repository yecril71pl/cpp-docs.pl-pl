---
title: GetProcAddress | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- GetProcAddress
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], GetProcAddress
- ordinal exports [C++]
- GetProcAddress method
ms.assetid: 48d14ae0-47ea-4c5d-96b1-2c158f1a26af
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 91fd6b983d648b682cbd60fa6126189e102b9f1c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43194362"
---
# <a name="getprocaddress"></a>GetProcAddress
Przetwarza jawne łączenie do wywołania biblioteki DLL [GetProcAddress](https://msdn.microsoft.com/library/windows/desktop/ms683212) celu uzyskania adresu eksportowanych funkcji w bibliotece DLL. Użyjesz wskaźnika zwróconej funkcji do wywołania funkcji DLL. **GetProcAddress** przyjmuje jako parametry uchwytu modułu DLL (zwrócone przez **LoadLibrary**, `AfxLoadLibrary`, lub **GetModuleHandle**) i przyjmuje nazwę funkcji, którą chcesz do wywołania lub liczbę porządkową eksportu funkcji.  
  
 Ponieważ wywołujesz funkcję DLL za pomocą wskaźnika i nie ma żadnych typów w czasie kompilacji sprawdzania, upewnij się, parametry funkcji są poprawne, tak aby nie przekroczyć pamięć umieszczonej na stosie i powodować naruszenie zasad dostępu. Jednym ze sposobów zapewnienia bezpieczeństwa typu jest Spójrz na prototypy funkcji eksportowanych funkcji i tworzenie pasujących definicji typów dla wskaźników funkcji. Na przykład:  
  
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
  
 Sposób określenia odpowiedniej funkcji podczas wywoływania **GetProcAddress** zależy sposób powstała biblioteki DLL.  
  
 Możesz uzyskać tylko Eksport porządkowej Jeśli tworzysz łącze do biblioteki DLL został utworzony przy użyciu pliku definicji (.def) modułu i jeżeli liczby porządkowe są wyszczególnione z funkcjami w **EKSPORTY** sekcji w pliku .def biblioteki DLL. Wywoływanie **GetProcAddress** z eksportową porządkową, w przeciwieństwie do nazwy funkcji, jest teraz nieco szybszy, jeśli biblioteka DLL ma wiele funkcji eksportowanych, ponieważ eksportowe liczebniki porządkowe służą jako indeksy do biblioteki DLL Eksportowanie tabeli. Z eksportowaną liczbą porządkową **GetProcAddress** może zlokalizować funkcje bezpośrednio w przeciwieństwie do porównywania określonej nazwy do nazw funkcji w tabeli eksportu biblioteki DLL. Jednakże, należy wywołać **GetProcAddress** z eksportowaną liczbą porządkową tylko wtedy, gdy masz kontrolę nad przypisywaniem liczb porządkowych do eksportowanych funkcji w pliku .def.  
  
## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?  
  
-   [Jak połączyć niejawnie biblioteki DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)  
  
-   [Określić, której metody łączenia użyjesz](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?  
  
-   [LoadLibrary i AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)  
  
-   [FreeLibrary](https://msdn.microsoft.com/library/windows/desktop/ms683152)  
  
-   [Eksportowanie z biblioteki DLL przy użyciu plików DEF](../build/exporting-from-a-dll-using-def-files.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteki DLL w programie Visual C++](../build/dlls-in-visual-cpp.md)