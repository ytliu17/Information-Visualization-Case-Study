# Improve the Information Visualization in a Popular Chinese App

## 1. Introduction

This article is about an information visualization case study.

After taking the information visualization course, we are very excited about the expertise learned in this field, and want to find and analyze some interesting visualizations shared publicly in the social media or academic communications. However, when we wanted to find some case studies on information visualization from the Internet, we were a little disappointed. Because most of the blogs and posts on this topic are about fancy and complex visualizations. Although they are really nice and enlightening, they are not very practical for us. As college students, we want to know how to make some basic visualizations better, such as line charts and histograms, to make our papers, presentations or even software more awesome and professional. Thus, we want to find simple and influential visualizations with some common mistakes.

Suddenly, it dawns on me that a visualization in an app we use every day can meet our requirements!

This is even more exciting! Case study about improving visualization in popular apps is not common, right? However, you may have never heard of this application, because it is for Chinese. Don't worry, I will clearly introduce you all about this visualization next!

## 2. Shanbei and the visualization

Shanbei is a mobile application used by Chinese to recite English words. "Shanbei" means "scallop", but its pronunciation in Chinese is the same as "good memory". Shanbei's function is to play words and let users choose "understand" or "hint", based on which the app decides whether to repeat the word afterwards. Its interface is shown in the figure below:

![app_interface](/pictures/0_interface_V1.png)

Because the language system is very different, it is really painful for Chinese students to memorize English words. Before this type of software, the word I was most familiar with was "abandon", because I was going to fall asleep when I started to learn the third word in the vocabulary list (I don’t know if friends from other countries have the same experience, maybe concentrating on learning is difficult for everyone). So this app is very popular in China, because it makes us learn English easier.

Now that you already know Shanbei, let's take a look at the visualization.

In order to allow users to memorize words more effectively, Shanbei draws each user's memory curve and compare it with the Ebbinghaus forgetting curve. The visualization is like this:

![visual_guid](/pictures/1_visual_guid_V1.png)

Because this mobile app is in portrait orientation and the chart is very long, the user must swipe the screen left and right to see the complete visualization. The following figure shows the complete visualization and sliding direction:

![visualization_Shanbei](/pictures/2_visualization_Shanbei_V2.png)

In the figure below, we have translated the Chinese in the visualization into English, and we guarantee that it does not matter if you do not understand the Chinese in other figures.

![visualization_Shanbei_translation](/pictures/3_visualization_Shanbei_translation_V1.png)

**If you look at the whole chart, I think you will definitely be confused by it, just like the first time we did.** This is why we chose this visualization. Indeed, it has an obvious drawback, but maybe more than that. Now, let us analyze and improve it!

## 3. Analysis and improvement

When we analyze the visualization, we must first determine the context of the visualization. The context of visualization mainly includes:

1. **Purpose:** What is the graph used for? (Exploratory or Descriptive?)
2. **Readership:** Who are the readers?
3. **Media:** In what media the graph is presented?
4. **Visual guides:** What other visual guides are offered to the readers?

First of all, the purpose of this visualization is to show the user the memory curve, not to explore the data. In other words, it is a descriptive visualization rather than an exploratory visualization, which means it must be of high quality. Secondly, it is presented in the Shanbei app, and its readers are Shanbei users. **It is worth noting that Shanbei is a portrait application.** Finally, as shown in the figure above, this visualization has no other visual guides, so we can focus on the chart.

In order to better analyze and improve this visualization, we replicated this chart with Python and matplotlib, as shown in the following figure:

![visualization_Shanbei_translation](/pictures/4_Figure_V2.png)

Now we can start to analyze it further! First of all, as you have discovered, the x-axis of the chart is uneven, which can confuse users, especially if they don't look at it carefully. However, as we mentioned in the previous section, Shanbei is a mobile portrait application, which means that the chart cannot be too long. That being the case, why don't we split it into two charts with uniform x-axis? Users can see the complete visualization without even swiping the screen!

![visualization_improvement_1](/pictures/5_improvement_1_1.png)

![visualization_improvement_1](/pictures/6_improvement_1_2.png)

Note that the gap on the x-axis in the first chart is one day, while in the second chart it is 30 days.

Now, we have solved the main problem. However, if you look at the chart and think carefully, you will find there is still a puzzling place. Since "N days later" is marked on the x-axis, why is the label of the first tick on the x-axis "today"? It would be more reasonable to change it to "0", right?

![visualization_improvement_2](/pictures/7_improvement_2_1.png)

In order to reduce the length, we will only show the first chart after the improvement.

Next, our work will be related to *cognitive psychology*, which attempts to explain human behavior by understanding thought processes. This is because visualization communicates information through visual elements, which means that good visualization must consider human memory and attention related to vision.

*Cognitive Tunneling* is one of the most important concept in the cognitive theory about information visualization. Cognitive tunneling is a mental state in which human brain focuses on a particular thing and does not see the rest of the environment, or other relevant data. Information visualizations should avoid unwanted cognitive tunneling. It supports many guidelines for effective visualizations. Here is one important guideline:

**Label elements directly, avoiding indirect look-up.** Use a legend only when space is tight. Cognitive tunnelling may naturally happen when looking at a visual element in the graph. If that happens, the user will not lose relevant information as long as the labels are close. If the user goes back and forth to the legend, it will have to process other elements in the graph which may overload the working memory.

So let's labele the curves directly.

![visualization_improvement_3](/pictures/8_improvement_3_1.png)

Then, we are going to deal with *chart junk*. Chart junk is visual elements in charts and graphs that are not necessary to comprehend the information represented on the graph or that distract the viewer from this information. Chart junk takes up readers' working memory and distracts their attention, making them unable to better obtain the information in the chart.

Maybe in the original visualization, grid (dotted lines and background) had to be used to guide users because of the length of the chart. But now, it does not make any sense, and we can remove it as chart junk!

![visualization_improvement_4](/pictures/9_improvement_4_1.png)

After that, let us consider a special problem, *color blindness*. It is estimated to affect 8% of men, and 0.5% of women. Red–green color blindness is the most common form, followed by blue–yellow color blindness, and total color blindness. One possible way to make things better is to use colorblind-friendly palettes, see <https://personal.sron.nl/~pault/>.

After Changing the color of the curves, we get the final visualization!

![final_visualization](/pictures/final_visualization_1.png)

![final_visualization](/pictures/final_visualization_2.png)

## 4. Summary and discussion

In the end, let us summarize what we have done:

1. Analyzed the context of the visualization;
2. Splitted the chart into two charts with uniform x-axis;
3. Changed the x tick label "today" to "0";
4. Labeled the curves directly;
5. Removed the grid and background;
6. Changed the color of the curves.

Now, we get a much better visualization.

However, think about it, is our improved visualization too simple? Is it really suitable as a visualization in an app? Can we add some decorative visual elements to make the visualization much more beautiful without reducing the readability so much? **Information visualization is also closely related to critical thinking and feedback!** We interviewed some of our classmates and they had different opinions, but most of them thought our work was very good. What is your opinion?
