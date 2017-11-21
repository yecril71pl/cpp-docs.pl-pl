---
title: "Zmienne środowiskowe | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: cl
dev_langs: C++
helpviewer_keywords:
- INCLUDE environment variable
- cl.exe compiler, environment variables
- LIBPATH environment variable
- environment variables, CL compiler
ms.assetid: 2606585b-a681-42ee-986e-1c9a2da32108
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ea0d0a3be8bdd87322958306cdaa3d581923739d
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="cl-environment-variables"></a>Zmienne środowiskowe CL

Narzędzia CL używa następujących zmiennych środowiskowych:

- CL i \_CL\_, jeśli została zdefiniowana. Narzędzia CL dołącza opcje i argumenty zdefiniowane w zmiennej środowiskowej CL do argumentów wiersza polecenia i dołącza opcje i argumenty zdefiniowane w \_CL\_, przed rozpoczęciem przetwarzania.

- OBEJMUJĄ, musi wskazywać podkatalogu \include instalację programu Visual C++.

- LIBPATH, który określa katalogi wyszukiwania plików metadanych przywoływana za pomocą [#using](../../preprocessor/hash-using-directive-cpp.md). Zobacz `#using` Aby uzyskać więcej informacji na temat LIBPATH.

Można ustawić CL lub \_CL\_ zmiennej środowiskowej, używając następującej składni:

> Ustaw CL = [[*opcji*]... [*pliku*]...] [/ link *opt łącze* ...]  
> Ustaw \_CL\_= [[*opcji*]... [*pliku*]...] [/ link *opt łącze* ...]

Aby uzyskać więcej informacji na temat argumentów do CL i \_CL\_ zmiennych środowiskowych, zobacz [składnia wiersza polecenia kompilatora](../../build/reference/compiler-command-line-syntax.md).

Możesz umożliwia zdefiniowanie plików i opcje, które najczęściej używane te zmienne środowiskowe i użyć wiersza polecenia, aby zdefiniować konkretne pliki i opcje do określonych celów. CL i \_CL\_ zmienne środowiskowe są ograniczone do 1024 znaków (wiersza polecenia limit wprowadzania).

Nie można użyć opcji /D do definiowania symbol, który używa znaku równości (=). Można zastąpić znak numeru (#) dla znaku równości. W ten sposób można użyć CL lub \_CL\_ zmienne środowiskowe do definiowania preprocesora stałe wartościami jawne — na przykład `/DDEBUG#1` do definiowania `DEBUG=1`.

Aby uzyskać odpowiednie informacje, zobacz [ustawić zmienne środowiskowe](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md).

## <a name="examples"></a>Przykłady

Poniżej przedstawiono przykładową konfigurację zmiennej środowiskowej CL:

> Ustaw CL = Zp2 OX /I\INCLUDE\MYINCLS \LIB\BINMODE. OBJ

Jeśli wartość tej zmiennej środowiskowej po wprowadzeniu `CL INPUT.C` w wierszu polecenia jest skuteczne polecenie:

> CL /Zp2 OX /I\INCLUDE\MYINCLS \LIB\BINMODE. WPROWADŹ LICZBĘ OBIEKTÓW. C

Poniższy przykład powoduje, że polecenie CL zwykły Kompiluj pliki źródłowe FILE1.c i FILE2.c, a następnie połącz plik obiektu FILE1.obj, FILE2.obj i FILE3.obj:

> CL ZESTAWU = FILE1. PLIK2 C. C  
> USTAW \_CL\_= PLIK3. OBJ  
> CL  

Ma to ten sam efekt co następującego polecenia:

> CL FILE1. PLIK2 C. PLIK3 C. OBJ

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)   
[Opcje kompilatora](../../build/reference/compiler-options.md)
