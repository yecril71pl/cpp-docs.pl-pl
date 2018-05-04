---
title: EKSPORTY | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 7cc7a9995fdc5be786712752e30015337b9f1607
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="exports"></a>EKSPORTY
Wprowadza sekcję definicje eksportu, określających wyeksportowanego nazwy lub porządkowe danych lub funkcji. Każda definicja musi być w oddzielnym wierszu.  
  
```  
EXPORTS  
   definition  
```  
  
## <a name="remarks"></a>Uwagi  
 Pierwszy `definition` może znajdować się na tej samej linii co `EXPORTS` — słowo kluczowe lub na kolejny wiersz. . DEF pliku może zawierać jeden lub więcej `EXPORTS` instrukcje.  
  
 Składnia eksportu `definition` jest:  
  
```  
  
entryname[=internalname] [@ordinal [NONAME]] [[PRIVATE] | [DATA]]  
```  
  
 `entryname` jest to nazwa funkcji lub zmienna, który chcesz wyeksportować. Jest to wymagane. Jeśli nazwa eksportowania różni się od nazwy w bibliotece DLL, określ nazwę eksportu w bibliotece DLL przy użyciu `internalname`. Na przykład, jeśli biblioteki DLL eksportuje funkcję `func1` i chcesz wywołań w celu używania go jako `func2`, należy określić:  
  
```  
EXPORTS  
   func2=func1  
```  
  
 Ponieważ nazwij dekorację jest używana przez kompilator Visual C++ dla funkcji języka C++, należy użyć jako nazwa `entryname` lub `internalname`, lub zdefiniuj eksportowane funkcje za pomocą `extern "C"` w kodzie źródłowym. Kompilator decorates również funkcje języka C, które używają [__stdcall](../../cpp/stdcall.md) wywoływanie Konwencji z prefiksem podkreślenia (_) i sufiks, który składa się z znak @ (@) następuje liczba bajtów (dziesiętna) na liście argumentów.  
  
 Aby znaleźć nazwy ozdobione generowane przez kompilator, użyj [DUMPBIN](../../build/reference/dumpbin-reference.md) narzędzia lub konsolidator [/MAP](../../build/reference/map-generate-mapfile.md) opcji. Nazwy ozdobione są specyficzne dla kompilatora. Podczas eksportowania nazwy ozdobione w. Plik DEF, pliki wykonywalne, która łączy do biblioteki DLL muszą zostać skompilowane również przy użyciu tej samej wersji kompilatora. Dzięki temu, że nazwy ozdobione w wywołującego odpowiadać nazwom wyeksportowanego w. DEF pliku.  
  
 Można użyć`ordinal` do określenia, czy numer, a nie nazwą funkcji, zostaną umieszczone w tabeli eksportu biblioteki DLL. Wiele bibliotek DLL systemu Windows wyeksportować porządkowe do obsługi starszego kodu. Było wspólnego do użycia porządkowe w 16-bitowy kod systemu Windows, ponieważ może pomóc zminimalizować rozmiar pliku dll. Nie zaleca się eksportowanie funkcji według liczby porządkowej, chyba że klientów biblioteki DLL potrzebne do obsługi starszych wersji. Ponieważ. LIB plik będzie zawierał mapowanie między numer porządkowy i funkcji, można użyć nazwy funkcji, jak zwykle w projektach, które używają biblioteki DLL.  
  
 Przy użyciu opcjonalnego `NONAME` — słowo kluczowe, możesz wyeksportować według liczby porządkowej tylko i zmniejszyć rozmiar tabeli eksportu w wynikowym pliku DLL. Jednak jeśli chcesz użyć [GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212.aspx) w pliku DLL, należy znać numer porządkowy, ponieważ nazwa nie jest prawidłowy.  
  
 Optional-słowo kluczowe `PRIVATE` uniemożliwia `entryname` zostaną uwzględnione w Biblioteka importowana, generowana przez łącze. Nie ma ona wpływu na eksportu w obrazie również generowany przez łącze.  
  
 Optional-słowo kluczowe `DATA` Określa, że eksportowania danych, nie kod. W tym przykładzie pokazano, jak można wyeksportować danych zmiennej o nazwie `exported_global`:  
  
```  
EXPORTS  
   exported_global DATA  
```  
  
 Istnieją cztery sposoby eksportowania definicję w kolejności zalecane:  
  
1.  [__Declspec(dllexport)](../../cpp/dllexport-dllimport.md) — słowo kluczowe w kodzie źródłowym  
  
2.  `EXPORTS` Oświadczenie. Plików DEF  
  
3.  [/EXPORT](../../build/reference/export-exports-a-function.md) Specyfikacja polecenia łącza  
  
4.  A [komentarz](../../preprocessor/comment-c-cpp.md) dyrektywy w kodzie źródłowym formularza `#pragma comment(linker, "/export: definition ")`  
  
 Wszystkie cztery metody można użyć w ten sam program. Gdy łącze tworzy program, który zawiera eksportu, tworzy również biblioteki importowanej, chyba że. EXP, plik jest używany w kompilacji.  
  
 Poniżej przedstawiono przykład sekcji eksportu:  
  
```  
EXPORTS  
   DllCanUnloadNow      @1          PRIVATE  
   DllWindowName = WindowName       DATA  
   DllGetClassObject    @4 NONAME   PRIVATE  
   DllRegisterServer    @7  
   DllUnregisterServer  
```  
  
 Podczas eksportowania zmienną z biblioteki DLL przy użyciu. Plik DEF, nie trzeba określić `__declspec(dllexport)` zmiennej. Jednak w pliku, który korzysta z biblioteki DLL, należy nadal używać `__declspec(dllimport)` w deklaracji danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Zasady dla instrukcji definicji modułu](../../build/reference/rules-for-module-definition-statements.md)