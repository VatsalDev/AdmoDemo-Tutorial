AdmoDemo-Tutorial
=================

demo of how to do AdMob integration In iOS


// In .h File

#import <UIKit/UIKit.h>
#import "GADBannerView.h"


@interface VatsDev : UIViewController<GADBannerViewDelegate> {
    
    GADBannerView *AbMob;
    
}
@property(nonatomic,strong) GADBannerView *bannerView;
-(GADRequest *)CreateRequest;


@end

# In .m File

#import "GADBannerView.h"
#import "GADRequest.h"

// After Importing this File 

- (void)viewDidLoad
{
    [super viewDidLoad];
    self.bannerView = [[GADBannerView alloc]
                       initWithFrame:CGRectMake(0.0,0.0, GAD_SIZE_320x50.width,GAD_SIZE_320x50.height)];
    
    self.bannerView.adUnitID = AdMob_ID;
 //   self.bannerView.delegate = self;
    self.bannerView.rootViewController = self;
    [self.view addSubview:self.bannerView];
    
    [self.bannerView loadRequest:[self CreateRequest]];
    
}

-(GADRequest *)CreateRequest
{
    GADRequest *request = [GADRequest request];
   // request.testDevices = [NSArray arrayWithObjects:GAD_SIMULATOR_ID,nil, nil];
    return  request;
}

-(void)adViewDidReceiveAd:(GADBannerView *)view
{
    [UIView animateWithDuration:1.0 animations:^{
        view.frame = CGRectMake(0.0, 0.0, view.frame.size.width, view.frame.size.height);
    }];
}

