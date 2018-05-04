---
title: -FS (Wymuś synchroniczne PDB zapisuje) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /FS
dev_langs:
- C++
helpviewer_keywords:
- -FS compiler option [C++]
- /FS compiler option [C++]
ms.assetid: b2caaffe-f6e1-4963-b068-648f06b105e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8565022a77742a1a8c7ed1f243a192d94c8627fb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="fs-force-synchronous-pdb-writes"></a>/FS (Wymuś synchroniczne zapisy do bazy PDB)
Wymusza zapisuje plik programu (PDB) bazy danych — utworzone przez [/zi](../../build/reference/z7-zi-zi-debug-information-format.md) lub [/zi](../../build/reference/z7-zi-zi-debug-information-format.md)— za pośrednictwem MSPDBSRV szeregowanie. WYWOŁANIE PLIKU EXE.  
  
## <a name="syntax"></a>Składnia  
  
```  
/FS  
```  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie gdy **/zi** lub **/zi** określono kompilator blokuje pliki PDB można zapisać informacji o typie i symboliczną informację o debugowaniu. To znacznie ograniczyć czas kompilatorowi generowanie informacji o typie, gdy jest duża liczba typów. Jeśli inny proces tymczasowo blokuje plik PDB — na przykład programu antywirusowego — zapisy przez kompilator może zakończyć się niepowodzeniem i może wystąpić błąd krytyczny. Ten problem może również się zdarzyć, gdy wiele kopii cl.exe dostępu do tego samego pliku PDB — na przykład, jeśli rozwiązania jest niezależna projektów, które korzystają z jednego pośredniego katalogów lub output katalogów, i równoległych kompilacji są włączone. **/FS** — opcja kompilatora uniemożliwia blokowanie pliku PDB kompilator i wymusza podąża MSPDBSRV. EXE, który serializuje dostępu. To może spowodować znaczne wydłużenie kompilacji, a nie uniemożliwia wszystkie błędy, które mogą wystąpić, gdy wiele wystąpień cl.exe dostępu do pliku PDB w tym samym czasie. Firma Microsoft zaleca zmianę rozwiązania, tak, aby projekty niezależne zapisu do oddzielania pośrednie i lokalizacji danych wyjściowych, lub wprowadzenia jednego z projektów zależny od innych w życie serializacji kompilacji projektu.  
  
 [/MP](../../build/reference/mp-build-with-multiple-processes.md) powoduje włączenie **/FS** domyślnie.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Wybierz **C/C++** folderu.  
  
3.  Wybierz **wiersza polecenia** strony właściwości.  
  
4.  Modyfikowanie **dodatkowe opcje** właściwości, aby uwzględnić `/FS` , a następnie wybierz **OK**.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)