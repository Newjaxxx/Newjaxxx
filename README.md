<h1 align="center">Hi 👋, I'm Newman</h1>
<h3 align="center">A passionate frontend developer</h3>

- 📫 How to reach me **acostanewman582@gmail.com**

<h3 align="left">Connect with me:</h3>
<p align="left">
<a href="https://twitter.com/acosta2gabriel" target="_blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/twitter.svg" target="_blank" alt="acosta2gabriel" height="30" width="40" /></a>
<a href="https://www.linkedin.com/in/newman-acosta/" target="_blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/linked-in-alt.svg" alt="https://www.linkedin.com/in/newman-acosta/" height="30" width="40" /></a>
<a href="https://www.facebook.com/profile.php?id=100010191168103" target="_blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/facebook.svg" alt="https://www.facebook.com/profile.php?id=100010191168103" height="30" width="40" /></a>
<a href="https://www.instagram.com/newman_ga/" target="_blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/instagram.svg" alt="https://www.instagram.com/newman_ga/" height="30" width="40" /></a>
</p>

<h3 align="left">Languages and Tools:</h3>
<p align="left"> <a href="https://www.w3schools.com/cpp/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/cplusplus/cplusplus-original.svg" alt="cplusplus" width="40" height="40"/> </a> <a href="https://www.w3schools.com/css/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/css3/css3-original-wordmark.svg" alt="css3" width="40" height="40"/> </a> <a href="https://git-scm.com/" target="_blank" rel="noreferrer"> <img src="https://www.vectorlogo.zone/logos/git-scm/git-scm-icon.svg" alt="git" width="40" height="40"/> </a> <a href="https://www.w3.org/html/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/html5/html5-original-wordmark.svg" alt="html5" width="40" height="40"/> </a> <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/javascript/javascript-original.svg" alt="javascript" width="40" height="40"/> </a> <a href="https://www.mysql.com/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mysql/mysql-original-wordmark.svg" alt="mysql" width="40" height="40"/> </a> <a href="https://www.photoshop.com/en" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/photoshop/photoshop-line.svg" alt="photoshop" width="40" height="40"/> </a> <a href="https://www.php.net" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/php/php-original.svg" alt="php" width="40" height="40"/> </a> <a href="https://reactjs.org/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/react/react-original-wordmark.svg" alt="react" width="40" height="40"/> </a> </p>

WITH stars AS (
    SELECT
        415460821 AS repo_id, IFNULL(COUNT(DISTINCT actor_login), 0) AS total
    FROM github_events
    WHERE
        type = 'WatchEvent'
        AND repo_id = 415460821
        AND action = 'started'
), commits AS (
    SELECT
        415460821 AS repo_id, IFNULL(SUM(push_distinct_size), 0) AS total
    FROM github_events
    WHERE
        type = 'PushEvent'
        AND repo_id = 415460821
), issues AS (
    SELECT
        415460821 AS repo_id, IFNULL(COUNT(DISTINCT number), 0) AS total
    FROM github_events
    WHERE
        type = 'IssuesEvent'
        AND repo_id = 415460821
), pull_request_creators AS (
    SELECT
        415460821 AS repo_id, IFNULL(COUNT(DISTINCT actor_login), 0) AS total
    FROM github_events
    WHERE
        type = 'PullRequestEvent'
        AND repo_id = 415460821
        AND action = 'opened'
)
SELECT
    415460821 AS repo_id,
    s.total AS stars,
    c.total AS commits,
    i.total AS issues,
    prc.total AS pull_request_creators
FROM (
    SELECT 415460821 AS repo_id
) sub
LEFT JOIN stars s ON sub.repo_id = s.repo_id
LEFT JOIN commits c ON sub.repo_id = c.repo_id
LEFT JOIN issues i ON sub.repo_id = i.repo_id
LEFT JOIN pull_request_creators prc ON sub.repo_id = prc.repo_id
;
