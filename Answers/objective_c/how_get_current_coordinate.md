## Как получить текущую координату?

[**Вернутся к списку вопросов**](https://github.com/Torlopov-Andrey/hh_interview_ios/blob/master/readme.md)

Получить текущую координату.

```Objective-C
- (void)getNearbyPlaces
{
   [self.placesClient currentPlaceWithCallback:^(GMSPlaceLikelihoodList * _Nullable likelihoodList, NSError * _Nullable error) {

   if (error != nil) {
        NSLog(@"Current Place error %@", [error localizedDescription]);
        return;
   }

   for (GMSPlaceLikelihood *likelihood in likelihoodList.likelihoods) {
         GMSPlace* place = likelihood.place;
         NSLog(@"Current Place name %@ at likelihood %g", place.name, likelihood.likelihood);
         NSLog(@"Current Place address %@", place.formattedAddress);
         NSLog(@"Current Place attributions %@", place.attributions);
         NSLog(@"Current PlaceID %@", place.placeID);
   }

   NSLog(@"likelihoodList = %@", likelihoodList);
   }];
}

self.placesClient = [GMSPlacesClient sharedClient];
```

[Ccылка на Google Places](https://developers.google.com/places/ios-api/start#add-a-place-picker)
