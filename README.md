# Rooba Finance Full Stack Role

## Name - Nikhil Yadav
## My self nikhil and i am a full stack web developer and blockchain enthusiast. I have more than 1 years of experience in web3.0. *Doing Internship at Autonomint ## (DEFI STABLE COIN PROTOCOL) *Experienced with DEX

## 1. Install NODE_MODULES of frontend and backend using "npm install" command

In the project directory, you can run:

### 2. Locate backend dir and start Server using "nodemon start" and after that `npm run start` to start Frontend

### TECK STACK

REACT
MONGODB
EXPRESS
NODE.js
Tailwind CSS

## Design Analysis and Implementation Strategy: 1. Understanding the Figma Design:
## 1.Complete Profile Page
![11](https://github.com/NikeVir/RoobaFinance/assets/82455622/be08bdaa-636b-4023-9ed9-cd427e816871)
![12](https://github.com/NikeVir/RoobaFinance/assets/82455622/af7f5bdf-07b6-40c9-946e-e6603f5d46df)
![13](https://github.com/NikeVir/RoobaFinance/assets/82455622/5f8360cd-6c11-492c-96f8-88d3b846c213)

## Question 2: React Form with Validation
## 1. Authentication with JWT and ERROR Handling
![14](https://github.com/NikeVir/RoobaFinance/assets/82455622/08921531-16de-4d78-90a5-acac8f159a1d)
![15](https://github.com/NikeVir/RoobaFinance/assets/82455622/1b6e055d-524a-47f3-9023-3397a6c4cc88)

## code :- 
  const handleSubmit = async (e) => {
    e.preventDefault();
    try {
      const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      if (!emailRegex.test(email)) {
        alert('Invalid email format. Please enter a valid email address.');
        return;
      }
      if (password.length < 8) {
        alert('Password must be at least 8 characters long.');
        return;
      }
      const response = await axios.post('http://localhost:8000/user/api/login', {
        email,
        password,
      });
      console.log(response.data.user)
      if (response.data.token) {

        localStorage.setItem('token', response.data.token);
        localStorage.setItem('userId', response.data.user._id);
        console.log('Login successful!');
        history('/');
      }
      else {
        alert(response.data.message);
      }
    } catch (error) {
      console.error('Login error:', error.message);
    }
  };

  

## Question 3: REST API with Node.js and Express
Problem Statement:
Task done - Succesfully

## Question 4: Express Middleware Creation
Problem Statement:
## code :-
const logRequest = (req, res, next) => {
    const timestamp = new Date().toISOString();
    const method = req.method;
    const url = req.url;
    const accessToken = req.headers['authorization'] || 'No Access Token';

    console.log(`[${timestamp}] ${method}: ${url}, AccessToken: "${accessToken}"`);

    next();
};


## Question 5: MongoDB Data Aggregation
Problem Statement:
const response = await User.aggregate([
        {
            $group: {
                _id: null,
                totalUsers: { $sum: 1 },
                averageAge: { $avg: "$age" },
                countries: {
                    $push: {
                        country: "$country",
                        count: 1
                    }
                }
            }
        },
        {
            $unwind: "$countries"
        },
        {
            $group: {
                _id: "$countries.country",
                totalUsers: { $sum: "$countries.count" },
                averageAge: { $avg: "$averageAge" }
            }
        },
        {
            $project: {
                _id: 0,
                country: "$_id",
                totalUsers: 1,
                averageAge: 1
            }
        }
    ])





