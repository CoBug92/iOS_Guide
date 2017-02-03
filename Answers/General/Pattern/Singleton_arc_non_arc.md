## Реализация синглтона в ARC и в non-ARC?

[**Вернутся к списку вопросов**](https://github.com/CoBug92/Interview_iOS/blob/master/README.md)

**ARC**
```objective-c
+ (CustomClass *)shared
{
    static CustomClass *singleton = nil;
    static dispatch_once_t onceToken;
    dispatch_once(&onceToken, ^{
        singleton = [[CustomClass alloc] init];
    });
    return singleton;
}
```

**NON-ARC**

`AppTools.h`
```Objective-C
@interface AppTools : NSObject {

    NSString *className;
}

@property ( nonatomic, retain ) NSString *className;

+ ( id ) sharedInstance;

@end    // AppTools
```


`AppTools.m`
```Objective-c
static AppTools *sharedAppToolsInstance = nil;

@implementation AppTools

@synthesize className;

- ( id ) init {

    self = [ super init ];
    if ( self ) {
        className = [ [ NSString alloc ] initWithString: @"AppTools" ];
    }
    return self;
}   // init

- ( void ) dealloc {

   // Should never be called, but just here for clarity really.
   [ className release ];
   [ super dealloc ];
}   // dealloc

+ ( id ) sharedInstance {

    @synchronized( self ) {
    if ( sharedAppToolsInstance == nil )
        sharedAppToolsInstance = [ [ super allocWithZone: NULL ] init ];
    }
    return sharedAppToolsInstance;
}   // sharedInstance

+ ( id ) allocWithZone: ( NSZone * )zone {

    return [ [ self sharedInstance ] retain ];
}   // allocWithZone:

- ( id ) copyWithZone: ( NSZone * )zone {

    return self;
}   // copyWithZone:

- ( id ) retain {

    return self;
}   // retain

- ( unsigned int ) retainCount {

    return UINT_MAX;    // denotes an object that cannot be released
}   // retainCount

- ( oneway void ) release {

    // never release
}   // release

- ( id ) autorelease {

    return self;
}   // autorelease
@end
```
