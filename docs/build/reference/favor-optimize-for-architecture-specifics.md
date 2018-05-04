---
title: -favor (Optymalizacja dla specyfiki architektury) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /favor
dev_langs:
- C++
helpviewer_keywords:
- -favor compiler option [C++]
- /favor compiler option [C++]
ms.assetid: ad264df2-e30f-4d68-8bd0-10d6bee71a2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 91f91373eef29adcb9a632e80520ed6713d3e39b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="favor-optimize-for-architecture-specifics"></a>/favor (optymalizacja pod kątem specyfiki architektury)
**/ favor:** `option` generuje kod, który jest zoptymalizowana dla określonej architektury lub kątem specyfiki architektury micro AMD i architektur firmy Intel.  
  
## <a name="syntax"></a>Składnia  
  
```  
/favor:{blend | ATOM | AMD64 | INTEL64}  
```  
  
## <a name="remarks"></a>Uwagi  
 **/favor:Blend**  
 generuje kod, który został zoptymalizowany pod kątem specyfiki architektury micro AMD i architektur firmy Intel, (x86 i x64). Gdy **/favor:blend** może nie być najlepszą wydajność możliwe na konkretny procesor, jest przeznaczony do zapewniają najlepszą wydajność tożsamość w szerokiej gamie x86 i x64 procesorów. Domyślnie **/favor:blend** jest włączona.  
  
 **/favor:Atom**  
 (x86 i x64) tworzy kod, który jest zoptymalizowana pod kątem specyfiki procesor Intel Atom i technologii Intel Centrino Atom. Kod, który jest generowany przy użyciu **/favor:ATOM** może również tworzyć instrukcji SSSE3 firmy Intel, SSE3 SSE2 i SSE instrukcje dotyczące procesory Intel.  
  
 **/favor:AMD64**  
 (tylko x64) optymalizuje wygenerowany kod dla AMD Opteron i Athlon procesorów, które obsługują rozszerzeń 64-bitowych. Kod zoptymalizowany można uruchamiać na x64 wszystkich platform zgodne. Kod, który jest generowany przy użyciu **/favor:AMD64** może spowodować zmniejszenie wydajności na procesory Intel, które obsługują Intel64.  
  
 **/favor:INTEL64**  
 (tylko x64) optymalizuje wygenerowany kod dla procesorów Intel, które obsługują Intel64, które zwykle zapewnia lepszą wydajność dla tej platformy. Wynikowy kod może działać na dowolnym x64 platformy. Kod, który jest generowany z **/favor:INTEL64** może spowodować zmniejszenie wydajności na AMD Opteron i Athlon procesorów, które obsługują rozszerzeń 64-bitowych.  
  
> [!NOTE]
>  Architektura Intel64 była wcześniej znana jako technologię Extended 64 pamięci i został odpowiedniej opcji kompilatora **/favor:EM64T**.  
  
 Aby uzyskać informacje dotyczące programu dla [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] architektury, zobacz [x64 konwencje kodowania](../../build/x64-software-conventions.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Wybierz **C/C++** folderu.  
  
3.  Wybierz **wiersza polecenia** strony właściwości.  
  
4.  Wybierz opcję kompilatora w **dodatkowe opcje** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)