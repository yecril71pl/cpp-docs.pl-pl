---
title: EKSPORTY | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/20/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- EXPORTS
dev_langs:
- C++
helpviewer_keywords:
- EXPORTS .def file statement
ms.assetid: dbcd7579-b855-44c4-bd27-931e157657f7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f6645ee4c890dab65cde8eab5dc18df1c31082c1
ms.sourcegitcommit: 7f3df9ff0310a4716b8136ca20deba699ca86c6c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2018
ms.locfileid: "42465841"
---
# <a name="exports"></a>EKSPORTY

Wprowadza sekcji definicji eksportu, które określają nazwy eksportowanych lub liczby porządkowe funkcji lub danych. Każda definicja musi być w oddzielnym wierszu.  
  
```DEF  
EXPORTS  
   definition  
```  
  
## <a name="remarks"></a>Uwagi  

Pierwszy *definicji* mogą znajdować się na tym samym wierszu co `EXPORTS` — słowo kluczowe lub na kolejny wiersz. . Plik DEF mogą zawierać jeden lub więcej `EXPORTS` instrukcji.  
  
Składnia służąca do eksportu *definicji* jest:  
  
```DEF
entryname[=internal_name|other_module.another_exported_name] [@Ordinal [NONAME]] [[PRIVATE] | [DATA]]
```

*Nazwa_wpisu* jest nazwa zmiennej lub funkcji, który chcesz wyeksportować. Jest to wymagane. Jeśli eksportujesz nazwa różni się od nazwy w bibliotece DLL, określ nazwę eksportu w bibliotece DLL, używając *internal_name*. Na przykład, jeśli biblioteka DLL eksportuje funkcję `func1` i wywołań, aby użyć go jako `func2`, należy określić:

```DEF
EXPORTS
   func2=func1
```

W przypadku nazwy, który eksportujesz z niektórych innych modułu, określ nazwę eksportu w bibliotece DLL, używając *other_module.exported_name*. Na przykład, jeśli biblioteka DLL eksportuje funkcję `other_module.func1` i wywołań, aby użyć go jako `func2`, należy określić:

```DEF
EXPORTS
   func2=other_module.func1
```

W przypadku nazwy, który eksportujesz z innego modułu, który eksportuje według liczby porządkowej, określ eksportu przez numer porządkowy w bibliotece DLL za pomocą *other_module. #ordinal_number*. Na przykład, jeśli biblioteka DLL eksportuje funkcję w module, gdzie jest numerem porządkowym 42, a ma obiektów wywołujących, aby użyć go jako `func2`, należy określić:

```DEF
EXPORTS
   func2=other_module.#42
```

Ponieważ kompilator języka Visual C++ używa dekorowania nazwy dla funkcji języka C++, możesz użyć internal_name również nazwę uzupełnioną lub zdefiniować eksportowane funkcji za pomocą funkcji extern "C" w kodzie źródłowym. Kompilator również rozszerza funkcje języka C, które używają [__stdcall](../../cpp/stdcall.md) Konwencji prefiks podkreślenia (_) i sufiks, który składa się z wywołania znakiem (@) następuje liczba bajtów (w zapisie dziesiętnym na liście argumentów).  
  
Aby znaleźć nazwy dekoracyjne wytworzone przez kompilator, użyj [DUMPBIN](../../build/reference/dumpbin-reference.md) narzędzia lub konsolidator [/MAP](../../build/reference/map-generate-mapfile.md) opcji. Nazwy ozdobione są specyficzne dla kompilatora. Jeśli eksportujesz nazwy dekorowane w. Plik DEF, pliki wykonywalne, które łącze do biblioteki DLL muszą być także kompilowane przy użyciu tej samej wersji kompilatora. Daje to gwarancję, że nazwy dekorowane w obiekcie wywołującym odpowiadały nazwom eksportowanym w. Plik DEF.  
  
Możesz użyć*porządkowe* do określenia, czy numer, a nie nazwę funkcji, zostaną umieszczone w tabeli eksportu biblioteki DLL. Wiele bibliotek DLL Windows wyeksportować liczb porządkowych do obsługi starszego kodu. Było często używa się w kodzie Windows 16-bitowych liczb porządkowych, ponieważ może to pomóc zminimalizować rozmiar biblioteki DLL. Nie zaleca się eksportowanie funkcji według liczby porządkowej, chyba że klientów biblioteki DLL potrzebny do obsługi starszych wersji. Ponieważ. Plik biblioteki będzie zawierać mapowania między numeru porządkowego a funkcją, można użyć nazwy funkcji, tak jak zwykle w projektach korzystających z biblioteki DLL.  
  
Przy użyciu opcjonalnego `NONAME` — słowo kluczowe, możesz wyeksportować według liczby porządkowej tylko i Zmniejsz rozmiar tabeli eksportu w wynikowy DLL. Jednakże jeśli chcesz używać [GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212.aspx) w pliku DLL, należy znać numer porządkowy, ponieważ nazwa straci ważność.  
  
Optional-słowo kluczowe `PRIVATE` zapobiega *Nazwa_wpisu* zostaną uwzględnione w Biblioteka importowana, generowana przez łącze. Nie ma ona wpływu na eksport na ilustracji, również jest generowany przez łącze.  
  
Optional-słowo kluczowe `DATA` Określa, że Eksport danych, a nie kod. Ten przykład przedstawia, jak można wyeksportować dane zmiennej o nazwie `exported_global`:  
  
```DEF  
EXPORTS  
   exported_global DATA  
```  
  
Istnieją cztery sposoby eksportowania definicji, wymienione w zalecanej kolejności:  
  
1.  [__Declspec(dllexport)](../../cpp/dllexport-dllimport.md) — słowo kluczowe w kodzie źródłowym  
  
2.  `EXPORTS` Instrukcji w. Plik DEF  
  
3.  [/EXPORT](../../build/reference/export-exports-a-function.md) specyfikacji za pomocą polecenia łącza  
  
4.  A [komentarz](../../preprocessor/comment-c-cpp.md) dyrektywę w kodzie źródłowym w formularzu `#pragma comment(linker, "/export: definition ")`  
  
Wszystkie cztery metody może służyć w tym samym programie. Łączenie kompilacji program, który zawiera eksporty, powoduje również utworzenie biblioteki importowanej, chyba że. EXP, plik jest używany w kompilacji.  
  
Oto przykład sekcji:  
  
```DEF  
EXPORTS  
   DllCanUnloadNow      @1          PRIVATE  
   DllWindowName = WindowName       DATA  
   DllGetClassObject    @4 NONAME   PRIVATE  
   DllRegisterServer    @7  
   DllUnregisterServer  
```  
  
Podczas eksportowania zmienną z biblioteki DLL za pomocą. Plik DEF, nie trzeba określić `__declspec(dllexport)` na zmiennej. Jednak w dowolnym pliku, który korzysta z biblioteki DLL, należy nadal używać `__declspec(dllimport)` w deklaracji danych.  
  
## <a name="see-also"></a>Zobacz także

[Zasady dla instrukcji definicji modułu](../../build/reference/rules-for-module-definition-statements.md)
