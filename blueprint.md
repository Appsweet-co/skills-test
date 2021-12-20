{{ template:logo }}

## Hi There! :wave:

Appsweet solves complex challenges for mobile apps. These apps are built on frameworks like Angular and Ionic. Past clients include pharmaceutical companies, sports leagues, and news outlets. 

We’re specialists in development and engineering with over over 12 years of experience. We write the code and that turns wireframes into working applications. We work inside and alongside our clients’ existing teams. Our apps meet industry standards for security and usability.

Visit our [GitHub](https://github.com/appsweet-co) page to see our open source projects.

## About This Test

This skills test is made up of 11 questions. These questions simulate real-world challenges. It lets us show you the types of things we solve for our clients, and lets you show us your creativity and style.

This is an “open book” test. There are many ways to solve these challenges. Please use all the tools and resources you would use for a real project. Ask us questions. Read our [Handbook](https://dperuo.gitbook.io/appsweet-handbook). View our [GitHub](https://github.com/appsweet-co) page.

Please submit your answers in a Markdown file hosted in a private GitHub Gist.

## Project Brief

### Client Profile

XYZ Healthcare is a large international healthcare provider. Many of their patients have chronic pain from Rheumatoid Arthritis. XYZ Healthcare believes tracking pain over time will lead to better pain management. Better pain management will increase quality of life for our client’s patients.

### Project Profile

XYZ Healthcare released a version of their pain app three years ago that solved for this use case:

```text
As a patient with Rheumatoid Arthritis
I want a mobile app that tracks my pain levels over time
So I can manage my pain better
```

Patients downloaded the app just over 17,000 since it was first released. The client considers this a success and now they want to release a new version with more features based on feedback from focus groups.

XYZ Healthcare will release the new version of the app in eight markets over three phases:

1. **Phase One:** United States, Germany, Brazil
1. **Phase Two:** Canada, France, Argentina
1. **Phase Three:** Mexico, Egypt

The client hired us to upgrade the app and oversee the market releases. Our deadline for Phase One release is the end of this year.

### End User Profile

End users for this app have Rheumatoid Arthritis (RA) in one or more joints of their body. Many of these patients have lived with RA for more than five years. Some patients were diagnosed within the last 12 months.

The age range for these patients is 35–65 years old. Most consider themselves “average” when it comes to using their mobile device.

### Tech Specs

The new version of the app must meet the following thecn specs:

1. Must support for iOS and Android devices.

1. Minimum OS versions:

    - iOS v13.x
    - Android v6.x

1. Must support Dark Mode.

1. Must follow all industry best practice for security and accessibility.

1. Must be easy to localize for the target markets.

## The Skills Test

Please write your answers in a Markdown file in a secret [GitHub gist](https://gist.github.com/). Send us the link when you’re ready for us to review your work.

### Q1. Project Dependencies

You looked at the codebase and saw that the app was built using Ionic v3 and Angular v5.

1. **What’s the cost-benefit analysis for the client if we upgrade to Ionic v5 and Angular v12?**
1. **What are three major changes between Ionic v3 and v5 we need to keep in mind while doing the upgrade?**
1. **What are three major changes between Angular v5 and v12 we need to keep in mind while doing the upgrade?**

### Q2. Custom Providers

You look deeper into the codebase and find the following method in one of the custom providers:

```ts
private sync(type: Type, data: any): Abstract {
  if (type === Type.NOTEBOOK) {
    return new Notebook(data, this.mobxStore, this.notebookProvider, this.consoleLogger);
  } else if (type === Type.NOTE) {
    return new Note(data, this.mobxStore, this.noteProvider, this.consoleLogger);
  } else if (type === Type.LOG) {
    return new Log(data, this.mobxStore, this.logProvider, this.consoleLogger);
  } else if (type === Type.FRIEND) {
    return new Friend(data, this.mobxStore, this.friendProvider, this.consoleLogger);
  } else if (type === Type.REQUEST) {
    return new Request(data, this.mobxStore, this.consoleLogger);
  } else if (type === Type.RECEIVED || type === Type.SENT) {
    return new Message(data, this.mobxStore, this.messageProvider, this.consoleLogger);
  } else if (type === Type.RESPONSE) {
    return new Survey(data, this.mobxStore, this.surveyProvider, this.consoleLogger);
  } else if (type === Type.EVENT_A) {
    return new EventA(data, this.mobxStore, this.consoleLogger);
  } else if (type === Type.EVENT_B) {
    return new EventB(data, this.mobxStore, this.consoleLogger);
  } else if (type === Type.EVENT_C) {
    return new EventC(data, this.mobxStore, this.consoleLogger);
  } else if (type === Type.EVENT_D) {
    return new EventD(data, this.mobxStore, this.consoleLogger);
  }
}
```

1. **Why might we consider this code brittle?**
1. **How would you make this code more robust?**

### Q3. Custom Pipes

You also found the following custom Angular Pipe:

```ts
export class ArticleFilterPipe implements PipeTransform {
  public transform(articles: Article[], illnessTypes: IllnessType[], categories: Array<{ readonly uuid: string; readonly name: string; }>) {
    if ((!illnessTypes || illnessTypes.length < 1) && (!categories || categories.length < 1)) {
      return articles;
    }

    const normalizedFilters = this.normalizeFilterCodes(illnessTypes);

    return articles.filter(article => {
      if (
        (categories.length > 0 && !Array.isArray(mobx.toJS(article.topicIds))) ||
        (illnessTypes.length > 0 && !Array.isArray(mobx.toJS(article.illnessTypeCode)))
      ) {
        return false;
      }

      return (
        (
          (categories.length > 0 && article.topicIds.some(topic => categories.some(category => category.uuid === topic))) ||
          (illnessTypes.length > 0 && article.illnessTypeCode.some(illnessTypeCode => normalizedFilters.some(filter => filter === illnessTypeCode)))
        )
      );
    });
  }
}
```

1. **Why might we consider this code brittle?**
1. **How would you make this code more robust?**

### Q4. App Performance

You load the app onto a real iPhone and Android device. The app feels sluggish and unresponsive on first launch.

1. **What might cause the app to feel slow?**
1. **How might you confirm your theory?**

### Q5. Broken CI Build

The client uses GitHub Actions as part of their automated build and deployment pipeline. You see the following error message on a failed build:

```text
Execution failed for task ':app:processDebugResources'.
> A failure occurred while executing com.android.build.gradle.internal.tasks.Workers$ActionFacade
   > Android resource linking failed
     /home/runner/.gradle/caches/transforms-2/files-2.1/227c80d4e01a4b4aa689685b88e9ffe9/core-1.7.0-beta02/res/values/values.xml:105:5-114:25: AAPT: error: resource android:attr/lStar not found.
```

1. **What’s the most likely cause of this error?**
1. **How might you fix it?**

### Q6. Hardware Support

The client says the new app must support the iPhone 5s for the Phase Two release.

1. **What do we need to keep in mind when supporting this hardware?**

### Q7. Data Encryption

The client says the new version must encrypt all its data. The app stores data locally on the device.

1. **What data encryption options do we have?**
1. **Which option is our best choice? Why?**

### Q8. Custom Stylesheet

You discover the following Sass file while refactoring the Dashboard page:

```scss
dashboard-page {
  button {
    ion-badge {
      position: absolute;
      top: -0.2rem;
      right: -0.2rem;
      opacity: 0.9;

      & ~ ion-icon {
        margin-right: 1.2rem;
      }
    }
  }

  .header-card {
    margin-top: 0;
    margin-bottom: 0;
    background-color: color($colors, background-grey);
    
    ion-card-content {
      padding: 0;
    }
  }
}
```

1. **Why might we consider this code brittle?**
1. **How would you make this code more robust?**

### Q9. UX Design

The current app makes users confirm certain actions (like deleting content) using alert dialogs. The client thinks switching to an ”undo“ feature might make for a better user experience.

1. **What are the benefits and tradeoffs of each type of UX?**
1. **How might you build an “undo” feature for the new version of the app?**

### Q10. Bluetooth Hardware

The client wants the new version of the app to sync with Bluetooth hardware like Fitbit and Google Fit. 

1. **What are three common issues mobile apps run into when syncing with Bluetooth hardware?**
1. **How might we mitigate these risks in our app?**

### Q11. Market Customization

The client says the app must have a password screen for the Argentina and Egypt  markets. Other markets don’t need a password screen for the app.

1. **What options do we have for adding an app password screen for the Argentina and Egypt markets only?**
1. **Which option is our best choice? Why?**

### Q12. Analytics

The client wants better analytics in the new version of the app. The client already use Adobe Analytics to track button clicks and page views. The client wants to continue using Adobe Analytics.

1. **What do we need to keep in mind when collecting better analytics data?**
1. **How might you build a more robust analytics tracking feature in the app?**

### Q13. User Notifications

The client want the new app to notify users if they haven’t opened the app in the last 10 days. Notification must happen even when the app is closed.

1. **What options do we have for adding notifications?**
1. **Which option is our best choice? Why?**

<!--
## Updating This README

We generate this README with the [@appnest/readme](https://github.com/andreasbm/readme) tool.
-->
