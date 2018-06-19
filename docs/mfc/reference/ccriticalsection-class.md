---
title: Klasa CCriticalSection | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCriticalSection
- AFXMT/CCriticalSection
- AFXMT/CCriticalSection::CCriticalSection
- AFXMT/CCriticalSection::Lock
- AFXMT/CCriticalSection::Unlock
- AFXMT/CCriticalSection::m_sect
dev_langs:
- C++
helpviewer_keywords:
- CCriticalSection [MFC], CCriticalSection
- CCriticalSection [MFC], Lock
- CCriticalSection [MFC], Unlock
- CCriticalSection [MFC], m_sect
ms.assetid: f776f74b-5b0b-4f32-9c13-2b8e4a0d7b2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1d6e713f6d5238d99af8f9311eb05a4b2dd39f7b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353908"
---
# <a name="ccriticalsection-class"></a>Klasa CCriticalSection
Reprezentuje "sekcja krytyczna" — obiektu synchronizacji, który umożliwia jeden wątek jednocześnie dostęp do zasobów lub sekcji kodu.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CCriticalSection : public CSyncObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CCriticalSection::CCriticalSection](#ccriticalsection)|Konstruuje `CCriticalSection` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CCriticalSection::Lock](#lock)|Umożliwia dostęp do `CCriticalSection` obiektu.|  
|[CCriticalSection::Unlock](#unlock)|Wersje `CCriticalSection` obiektu.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CCriticalSection::operator CRITICAL_SECTION *](#operator_critical_section_star)|Pobiera wskaźnik do wewnętrznej **CRITICAL_SECTION** obiektu.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CCriticalSection::m_sect](#m_sect)|A **CRITICAL_SECTION** obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Sekcje krytyczne są przydatne, jeśli tylko jeden wątek jednocześnie można mogą modyfikować dane i kontrolowane zasobów. Na przykład dodawania węzłów do połączonej listy jest procesem, powinien być dozwolony tylko przez jeden wątek na raz. Za pomocą `CCriticalSection` obiekt do kontrolowania listy połączonej, tylko jeden wątek jednocześnie uzyskać dostęp do listy.  
  
> [!NOTE]
>  Funkcje `CCriticalSection` klasy są dostarczane przez rzeczywiste Win32 **CRITICAL_SECTION** obiektu.  
  
 Sekcje krytyczne są używane zamiast muteksy (zobacz [CMutex](../../mfc/reference/cmutex-class.md)) gdy szybkość jest krytyczne i zasobu nie będzie można użyć poza granicami procesu.  
  
 Istnieją dwie metody przy użyciu `CCriticalSection` obiektu: autonomiczne i osadzone w klasie.  
  
-   Autonomiczny metoda do użycia autonomicznego `CCriticalSection` obiektów, utworzyć `CCriticalSection` obiektu, gdy jest to potrzebne. Po pomyślnym zwrotu z konstruktora, jawnie zablokować dostęp do obiektu o wywołaniu [blokady](#lock). Wywołanie [Unlock](#unlock) po zakończeniu uzyskiwanie dostępu do sekcji krytycznych. Ta metoda podczas jaśniejszy osobie odczytywania kodu źródłowego, jest bardziej podatne na błędy, ponieważ należy pamiętać zablokować i odblokować sekcja krytyczna przed i po nich dostępu.  
  
     Jednak bardziej preferowaną metodą jest użycie [CSingleLock](../../mfc/reference/csinglelock-class.md) klasy. Obejmuje ona również `Lock` i `Unlock` metody, ale nie trzeba się martwić o odblokowanie zasobu w przypadku wystąpienia wyjątku.  
  
-   Osadzona metoda klasy mogą również współużytkować z wielu wątków, dodając `CCriticalSection`— element członkowski danych typu klasy i blokowanie element członkowski danych w razie potrzeby.  
  
 Aby uzyskać więcej informacji na temat używania `CCriticalSection` obiektów, zobacz artykuł [Multithreading: jak używać klas synchronizacji](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CCriticalSection`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxmt.h  
  
##  <a name="ccriticalsection"></a>  CCriticalSection::CCriticalSection  
 Konstruuje `CCriticalSection` obiektu.  
  
```  
CCriticalSection();
```  
  
### <a name="remarks"></a>Uwagi  
 Dostęp, lub zwolnij `CCriticalSection` obiektów, Utwórz [CSingleLock](../../mfc/reference/csinglelock-class.md) obiekt i wywołanie jego [blokady](../../mfc/reference/csinglelock-class.md#lock) i [Unlock](../../mfc/reference/csinglelock-class.md#unlock) funkcji elementów członkowskich. Jeśli `CCriticalSection` obiekt jest używany autonomiczny, wywołaj jego [Unlock](#unlock) funkcji członkowskiej do jego zwolnienia.  
  
 Jeśli konstruktora nie powiedzie się można przydzielić pamięci wymagany system, wyjątek pamięci (typu [CMemoryException](../../mfc/reference/cmemoryexception-class.md)) jest automatycznie generowany.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CCriticalSection::Lock](#lock).  
  
##  <a name="lock"></a>  CCriticalSection::Lock  
 Wywołanie tej funkcji Członkowskich uzyskanie dostępu do obiektu sekcja krytyczna.  
  
```  
BOOL Lock();  
BOOL Lock(DWORD dwTimeout);
```  
  
### <a name="parameters"></a>Parametry  
 `dwTimeout`  
 `Lock` ignoruje wartości tego parametru.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli funkcja zakończyło się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 `Lock` to blokującego wywołanie, którego nie będzie zwracać, dopóki nie zostanie zasygnalizowane obiektu sekcja krytyczna (staje się dostępna).  
  
 Jeśli konieczne jest czas oczekiwania, można użyć [CMutex](../../mfc/reference/cmutex-class.md) obiekt zamiast `CCriticalSection` obiektu.  
  
 Jeśli `Lock` nie powiedzie się, można przydzielić pamięci systemu niezbędne, wyjątek pamięci (typu [CMemoryException](../../mfc/reference/cmemoryexception-class.md)) jest automatycznie generowany.  
  
### <a name="example"></a>Przykład  
 W przykładzie pokazano podejście zagnieżdżonej sekcji krytycznej kontrolowanie dostępu do zasobu udostępnionego (statycznych `_strShared` obiektu) za pomocą udostępnionej `CCriticalSection` obiektu. `SomeMethod` Funkcja pokazuje aktualizowania zasobu udostępnionego w bezpieczny sposób.  
  
 [!code-cpp[NVC_MFC_Utilities#11](../../mfc/codesnippet/cpp/ccriticalsection-class_1.h)]  
  
##  <a name="m_sect"></a>  CCriticalSection::m_sect  
 Zawiera obiekt sekcja krytyczna, który jest używany przez wszystkie `CCriticalSection` metody.  
  
```  
CRITICAL_SECTION m_sect;  
```  
  
##  <a name="operator_critical_section_star"></a>  CCriticalSection::operator CRITICAL_SECTION *  
 Pobiera **CRITICAL_SECTION** obiektu.  
  
```  
operator CRITICAL_SECTION*();
```   
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji można pobrać wskaźnik do wewnętrznej **CRITICAL_SECTION** obiektu.  
  
##  <a name="unlock"></a>  CCriticalSection::Unlock  
 Wersje `CCriticalSection` obiekt do użycia przez inny wątek.  
  
```  
BOOL Unlock();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli podano niezerowe `CCriticalSection` wątek został właścicielem obiektu i wersji został pomyślnie; w przeciwnym razie wartość 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `CCriticalSection` jest używany autonomiczny, `Unlock` musi zostać wywołany bezpośrednio po zakończeniu korzystania z zasobów kontrolowane przez sekcja krytyczna. Jeśli [CSingleLock](../../mfc/reference/csinglelock-class.md) obiektu jest używana, `CCriticalSection::Unlock` zostanie wywołana przez obiekt blokady `Unlock` funkcję elementu członkowskiego.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CCriticalSection::Lock](#lock).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CSyncObject](../../mfc/reference/csyncobject-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CMutex](../../mfc/reference/cmutex-class.md)
