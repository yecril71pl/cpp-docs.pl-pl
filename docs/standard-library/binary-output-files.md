---
title: "Wyjściowe pliki binarne | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- I/O [C++], binary output files
- files [C++], binary output files
- binary data, binary output files
ms.assetid: 180954af-8cd6-444b-9a76-2f630a3389d8
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: da2d0ac01919773492f075f2e2dd6a7d210224fb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="binary-output-files"></a>Binarne pliki wyjściowe
Strumienie pierwotnie zostały zaprojektowane dla tekstu, więc tekst jest to domyślny tryb danych wyjściowych. W trybie tekstu znaku nowego wiersza (10 szesnastkowe) rozwijany do karetki return-wysuwu wiersza (tylko 16-bitowe). Rozszerzenie może spowodować problemy, jak pokazano poniżej:  
  
```  
// binary_output_files.cpp  
// compile with: /EHsc  
#include <fstream>  
using namespace std;  
int iarray[2] = { 99, 10 };  
int main( )  
{  
    ofstream os( "test.dat" );  
    os.write( (char *) iarray, sizeof( iarray ) );  
}  
```  
  
 Mogą wymagać tego programu do wyjściowego sekwencji bajtów {99, 0, 10, 0}; Zamiast tego należy go generuje {99, 0, 13, 10, 0}, która powoduje występowanie problemów programu oczekiwano binarne dane wejściowe. Jeśli konieczne true binarne dane wyjściowe, w którym są zapisywane znaków niezrozumiały, można określić formatu binarnego przy użyciu [ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream) Konstruktor openmode argumentu:  
  
```  
// binary_output_files2.cpp  
// compile with: /EHsc  
#include <fstream>  
using namespace std;  
int iarray[2] = { 99, 10 };  
  
int main()  
{  
   ofstream ofs ( "test.dat", ios_base::binary );  
  
   // Exactly 8 bytes written  
   ofs.write( (char*)&iarray[0], sizeof(int)*2 );   
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Strumienie wyjściowe](../standard-library/output-streams.md)

