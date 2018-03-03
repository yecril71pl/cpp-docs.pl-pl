---
title: "-H (Ograniczaj długość nazw zewnętrznych) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /h
dev_langs:
- C++
helpviewer_keywords:
- public name length
- /H compiler option [C++]
- H compiler option [C++]
- external names
- -H compiler option [C++]
ms.assetid: de701dd3-ed04-4c88-8195-960d2520ec2e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4d5e862eb8e45d1f2558592c0bb54c1adb9305f7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="h-restrict-length-of-external-names"></a>/H (Ograniczaj długość nazw zewnętrznych)
Przestarzałe. Ogranicza długość nazw zewnętrznych.  
  
## <a name="syntax"></a>Składnia  
  
```  
/Hnumber  
```  
  
## <a name="arguments"></a>Argumenty  
 `number`  
 Określa maksymalną długość nazw zewnętrznych dozwolone w programie.  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie długość nazw zewnętrznych (publicznych) to 2,047 znaków. Dotyczy to programów C i C++. Przy użyciu **/H** można jedynie zmniejszyć maksymalną dozwoloną długość identyfikatorów, nie powinna ona być. Odstęp między **/H** i `number` jest opcjonalna.  
  
 Jeśli program zawiera zewnętrznej nazwy dłuższe niż `number`, dodatkowe znaki zostaną zignorowane. Jeśli kompilacja programu bez **/H** i jeśli identyfikator zawiera więcej niż 2,047 znaków, kompilator generuje [krytyczny błąd C1064](../../error-messages/compiler-errors-1/fatal-error-c1064.md).  
  
 Limit długości zawiera wszystkie utworzone przez kompilator wiodące podkreślenia (_) lub znak @ (@). Następujące znaki są częścią identyfikatora i podejmij znaczących lokalizacji.  
  
-   Kompilator dodaje wiodące podkreślenia (_) do nazwy zmodyfikowany przez `__cdecl` (ustawienie domyślne) i `__stdcall` Konwencje wywoływania oraz wiodącego znak (@) do nazw zmodyfikowany przez `__fastcall` konwencji wywoływania.  
  
-   Kompilator dołącza informacje o rozmiarze argument nazwy zmodyfikowany przez `__fastcall` i `__stdcall` konwencji wywoływania i dodaje informacje o typie, do nazwy C++.  
  
 Może się okazać **/H** przydatne:  
  
-   Podczas tworzenia wielu języków lub przenośne programy.  
  
-   Jeśli używasz narzędzia, które nakładają limit długości zewnętrznych identyfikatorów.  
  
-   Jeśli chcesz ograniczyć ilość miejsca używanego przez symbole kompilacji debugowania.  
  
 W poniższym przykładzie przedstawiono sposób przy użyciu **/H** faktycznie może powodować błędy, jeśli identyfikator długości są ograniczone zbyt dużo:  
  
```cpp  
// compiler_option_H.cpp  
// compile with: /H5  
// processor: x86  
// LNK2005 expected  
void func1(void);  
void func2(void);  
  
int main() { func1(); }  
  
void func1(void) {}  
void func2(void) {}  
```  
  
 Ponadto należy zachować ostrożność, korzystając z **/H** opcji z powodu kompilatora wstępnie zdefiniowane identyfikatory. Jeśli długość maksymalna identyfikator jest za mały, niektórych wstępnie zdefiniowane identyfikatory będzie biblioteki nierozwiązane, jak również niektórych wywołania funkcji. Na przykład jeśli `printf` funkcja jest używana wraz z opcją **/H5** określono w czasie kompilacji, symbol **_prin** zostaną utworzone w celu odwołania `printf`, to nie zostanie znalezione w bibliotece.  
  
 Użycie **/H** jest niezgodny z [/GL (optymalizacja całego programu)](../../build/reference/gl-whole-program-optimization.md).  
  
 **/H** od wersji programu Visual Studio 2005 za przestarzały opcja; zwiększono maksymalną długość limity i **/H** nie jest już potrzebne. Listę opcji kompilatora przestarzałe, zobacz **uznane za przestarzałe i usunąć — opcje kompilatora** w [kompilatora opcje rozbiciu na kategorie](../../build/reference/compiler-options-listed-by-category.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **wiersza polecenia** strony właściwości.  
  
4.  Typ opcji kompilatora w **dodatkowe opcje** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)