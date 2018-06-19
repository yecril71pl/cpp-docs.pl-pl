---
title: -QIfist (pomijanie _ftol) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /qifist
dev_langs:
- C++
helpviewer_keywords:
- QIfist compiler option [C++]
- -QIfist compiler option [C++]
- /QIfist compiler option [C++]
ms.assetid: 1afd32a5-f658-4b66-85f4-e0ce4cb955bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 77ec65e330cebb1de718330ba129e960383b31c6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378408"
---
# <a name="qifist-suppress-ftol"></a>/QIfist (Pomijanie _ftol)
Przestarzałe. Pomija wywołanie funkcji Pomocnik `_ftol` podczas konwersji z typu zmiennoprzecinkowego na typ całkowity jest wymagana.  
  
## <a name="syntax"></a>Składnia  
  
```  
/QIfist  
```  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  **/ QIfist** jest dostępna tylko w kompilatora przeznaczonych dla x86; tej opcji kompilatora nie jest dostępna w kompilatory przeznaczonych dla [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] orARM.  
  
 Oprócz konwertowania na typ całkowity, typ zmiennoprzecinkowy `_ftol` funkcja zapewnia trybu zaokrąglania jednostki liczb zmiennoprzecinkowych (FPU) kierunku zera (truncate), ustawiając bity 10 i 11 słowa formantu. Gwarantuje to, że typ zmiennoprzecinkowy konwertowania na typ całkowity występuje zgodnie z opisem standardu ANSI C (odrzucone ułamkową część liczby). Korzystając z **/QIfist**, nie ma zastosowania gwarancji. Tryb zaokrąglania będzie jedną z czterech zgodnie z opisem w instrukcji obsługi Intel:  
  
-   Zaokrąglona do najbliższej (parzystą liczbą Jeśli jednakowo odległych)  
  
-   Zaokrąglij w kierunku nieskończoności ujemnej  
  
-   Zaokrąglij do nieskończoności dodatniej  
  
-   Zaokrąglij w kierunku zera.  
  
 Można użyć [_control87 —, _controlfp —, \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md) funkcji C-Run-Time, aby zmodyfikować zachowanie zaokrąglania FPU. Domyślny tryb FPU zaokrąglania jest "Zaokrąglona do najbliższej." Przy użyciu **/QIfist** może poprawić wydajność aplikacji, ale nie bez ryzyka. Należy dokładnie przetestować części kodu, które są wrażliwe na zaokrąglania tryby przed zależne od kodu skompilowanej za pomocą **/QIfist** w środowiskach produkcyjnych.  
  
 [/ arch (x86)](../../build/reference/arch-x86.md) i **/QIfist** nie można użyć w tym samym compiland.  
  
> [!NOTE]
>  **/ QIfist** jest obowiązująca domyślnie ponieważ zaokrąglania bits również wpływ liczba zmiennoprzecinkowa na liczby zmiennoprzecinkowe wskazuje zaokrąglania (co ma miejsce po każdym obliczeniu), więc po ustawieniu flagi zaokrąglania stylu języka C (w stronę zera) z liczby zmiennoprzecinkowej obliczenia mogą się różnić. **/ QIfist** nie powinny być używane, jeśli kod zależy od oczekiwanego zachowania obcinanie ułamkową część liczby zmiennoprzecinkowej. Jeśli nie wiesz, nie używaj **/QIfist**.  
  
 **/QIfist** opcji jest przestarzały, począwszy od programu Visual Studio 2005. Kompilator wprowadził lepsza float int szybkości konwersji. Listę opcji kompilatora przestarzałe, zobacz **uznane za przestarzałe i usunąć — opcje kompilatora** w [kompilatora opcje rozbiciu na kategorie](../../build/reference/compiler-options-listed-by-category.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **wiersza polecenia** strony właściwości.  
  
4.  Typ opcji kompilatora w **dodatkowe opcje** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [/Q opcje (operacje na niskim poziomie)](../../build/reference/q-options-low-level-operations.md)   
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)