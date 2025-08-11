# sandragesing.github.io
Sandra Gesing's website

## How to Update Content

Most of the content is controlled by the data in the `data` directory and then rendered through a shortcode in the templates directory.

Each json file has slight variations to represent each page's unique structure and there are changes in the shortcodes to accommodate the different structures.

In total there are Json files encoding data for publications, work experience, education, research visits, each year of lectures, professional services, current projects, previous projects, current funding and previous funding.

To add new content to any of these sections, simply add a new json object to the appropriate json file. 

### Adding a new publication

The publications json is the largest. It has a key-value pair for the year and an array of publications. Each publication is comprised of three main parts: authors, link, and title. There is then a url key-value pair which is applied to the link value in the shortcode. Finally there is the tags section. This controls whether the publication appears in a section such as journals, peer-reviewed conferences etc.

The recognized tags are:

- journal
- conference
- edited
- misc
- white-paper
- book
- special

If a publication is not tagged it will appear in the all publications section.

This is an example of a publication object:

{
    "year": 2025,
    "publications": [
        {
            "authors": "List of authors",
            "link": "Link",
            "title": "Title, sometimes just whatever text comes after the link",
            "url": "url applied to link", 
            "tags": ["journal"]
        },
        {
            "authors":"S. Gesing, K. Kee, S. Brandt, S. Cleveland, S. Bradley, J. Smith, B. Villegas Martinez (2025)",
            "link":"How to Position Your Gateway for Failure: The Ten Don’ts of Gateway Design",
            "title":"HICSS-58 (58th Hawaii International Conference on System Sciences), Big Island, HI, January 2025",
            "url":"https://scholarspace.manoa.hawaii.edu/items/636b980c-01b5-4737-9139-02189047851c"
            ,"tags": ["conference"]
        }
    ]               
}

### Adding a new work experience

The work experience json file is structured in the following way:

{
    "title": "title",
    "description": "description",
    "links": [
        {
            "url": "url",
            "text": "text"
        }
    ],
    "roles": [
        "role"
    ]
},
{
    "title": "US Research Software Engineers Association (US-RSE)",
    "description": "since 2023",
    "links": [
        {
            "url": "https://us-rse.org/",
            "text": "US Research Software Engineers Association (US-RSE)"
        }
    ],
    "roles": [
        "Executive Director"
    ]
}

The main parts are the title and description. The links array specifies any part of the title that should have a link. You can include multiple links in the array, just specify the text that should be linked and the url it should be linked with. The roles array displays the one or multiple roles associated, this will be rendered in bold by default.

### Adding a new education

The educations json file is structured the same as the work experience json file, however there is no roles field.

{
    "title": "title",
    "description": "description",
    "links": [
        {
            "url": "url",
            "text": "text"
        }
    ]
},
{
    "title": "PhD in Computer Science",
    "description": "2023 - 2025",
    "links": [
        {
            "url": "https://www.cs.ubc.ca/",
            "text": "University of British Columbia"
        }
    ]
}


### Adding a new research visit

The research visits json file is structured the exact same as the education json file. 

### Adding a new project

There are two projects json files. one for current projects and one for previous projects. The current projects json file is structured more simply and thus uses a different format and shortcode.

Current projects json file:

{
    "title": "title",
    "description": "description",
    "url": "url",
},

The url is applied to the entire title by default.

By contrast, the previous projects json file is structured with the links array and the rows array. 

{
    "title": "title",
    "description": "description",
    "links": [
        {
            "url": "url",
            "text": "text"
        }
    ],
    "rows": [
        {
            "title": "title",
            "description": "description",
            "url": "url"
        }
    ]
}

The links array specifies any part of the title that should have a link with a series of json objects that specify the text and the associated url.
The rows array contins json objects that are similar to the current projects json file. Simply specify the title, description, and url. The url is applied to the entire title by default.

### Adding a new funding

The current and previous funding json files are very simple and are strcutred the same as the current projects json file.

There is simply a title, description, and url field. The url is applied to the entire title by default.

### Adding a new lecture

The lectures json file is structured in a similar way to the previous projects json file. The only difference is that there is no rows array.

There is simply a title, description, and links array to specify any part of the title that should have a link. 

Note that the description text is simply rendered smaller than the title text.

### Adding a new professional service

The professional services json file is the most complex. It is structured in the following way:


[
  {
    "category": "Professional affiliations",
    "rows": [
      {
        "title": "AGU",
        "description": "2022, 2020, 2018, 2016",
        "url": "https://sites.agu.org/",
        "sub_entries": []
      },
      {
        "title": "IEEE",
        "description": "2014-2021",
        "url": "http://www.ieee.org/index.html",
        "sub_entries": [
          {
            "title": "IEEE Computer Society",
            "description": "",
            "url": "https://www.computer.org/portal/web/guest/home"
          },
          {
            "title": "IEEE Technical Committee on Scalable Computing (TCSC)",
            "description": "",
            "url": "https://www.ieeetcsc.org/"
          },
          {
            "title": "Coordinator and chair of the IEEE Technical Area on Science Gateways",
            "description": "2014-2021",
            "url": "http://ieeesciencegateways.org/"
          }
        ]
      }
    ]
  },
  {
    "category": "Funding agencies",
    "rows": [
      {
        "title": "NSF review panel",
        "description": "2024, 2022, 2020, 2018, 2016",
        "url": "http://www.nsf.gov/",
        "sub_entries": []
      },
    ]
  }
]

As you can see we have different categories which determines the table that the entries are rendered in. In each row there is a title, description, url, and sub_entries array. The description is mainly used for the years. The url is applied to the title as usual. In some cases such as with IEEE. There are sub entires which can be added in the sub_entries array section with the usual title description and url format.
