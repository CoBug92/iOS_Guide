## Как добавить свойство в существующий объект с закрытой реализацией через runtime?

[**Вернутся к списку вопросов**](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/readme.md)

Добавляем свойство в GMSPlace. Добавляем shortAddress через runtime.
```Objective_c
#import <GoogleMaps/GoogleMaps.h>
@interface GMSPlaceategory)
@property (strong, nonatomic) NSString *shortAddress;
@end
#import "GMSPlace+Category.h"
#import <objc/runtime.h>

@implementation GMSPlace (Category)
- (NSString*) shortAddress {
    return objc_getAssociatedObject(self, @selector(shortAddress));
}
- (void)setShortAddress:(NSString *)shortAddress {
    objc_setAssociatedObject(self, @selector(shortAddress), shortAddress, OBJC_ASSOCIATION_RETAIN_NONATOMIC);
}
@end
```
